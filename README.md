# Ansible Sixpack Role

An [Ansible Role](http://docs.ansible.com/playbooks_roles.html) for setting up a
[Sixpack](http://sixpack.seatgeek.com/) server.

The role handles installing the following (In order of installation):

- Nginx
- Redis
- Sixpack

Any of these can be removed by commenting out, or removing the line from `tasks/main.yml`.

## Configuration

- **Ansible Role Variables:** `vars/main.yml`.
- **Sixpack Config:** `templates/config.yml`

## Sixpack Server

The server is deployed behind an Nginx Proxy (optionally using SSL).  It also
handles all of the CORS headers automatically for you.

## Sixpack Web Interface

The web interface is deployed behind an Nginx Proxy.

### Authentication

HTTP Authentication is enabled for the web interface as a quick means of
protecting the interface.

The defaults are:

- **Username:** sixpack
- **Password:** sixpack

You can and *should* change these.  You can modify it by using `htpasswd`:

	htpasswd -c .htpasswd sixpack

Enter the new password when prompted.

**Note: In production, you might want to only allow certain IP addresses access
to the web interface.**
