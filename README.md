# docker-gerrit-openldap-phpldapadmin-test

Docker setup including an OpenLDAP server, a phpldapadmin box and a Gerrit
instance.

Run it with `docker-compose up`.

After that go to `http://localhost:8080` and login with the `admin` Gerrit user
(password is `admin`). (The first user to log into Gerrit becomes an
administrator). There is another user called `user` (password `user`).

Make sure to add an SSH key for each user. When testing all user can use the
same SSH key.

There is an `openldap.ldif` files which is fed to the OpenLDAP server at
startup. Add more users, groups, etc. there.

Then access the `gerrit` CLI like this

```
ssh -p 29418 admin@localhost gerrit --help
```

To create a project

```
ssh -p 29418 admin@localhost gerrit create-project test --empty-commit
```

To clone the project locally and install Gerrit's commit message hook

```
git clone ssh://user@localhost:29418/test.git
cd test
mkdir -p .git/hooks
scp -pP 29418 user@localhost:hooks/commit-msg .git/hooks/
```

When testing locally commit by specifying the author like this

```
git -c 'user.name=user' -c 'user.email=user@test' commit -m ...
```
