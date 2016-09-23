# docker-gerrit-openldap-phpldapadmin-test

Docker setup including an OpenLDAP server, a phpldapadmin box and a Gerrit
instance.

Run it with `docker-compose up`.

After that go to `http://localhost:8080` and login with the `admin` Gerrit user
(password is `admin`). (The first user to log into Gerrit becomes an
administrator). There is another user called `user` (password `user`).

There is an `openldap.ldif` files which is fed to the OpenLDAP server at
startup. Add more users, groups, etc. there.
