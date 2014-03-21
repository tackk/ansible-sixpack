# Ansible Sixpack Role

An [Ansible Role](http://docs.ansible.com/playbooks_roles.html) for setting up a
[Sixpack](http://sixpack.seatgeek.com/) server.

The role handles installing the following (In order of installation):

- Nginx
- Redis
- Sixpack

## Details

The Role sets up 2 Nginx Sites: One for the Sixpack Server, and one for the web
interface.

### Configuration

All configuration of the Role is done in `vars/main.yml`.

### Sixpack Server

The server is deployed behind an Nginx Proxy (optionally using SSL).  It also
handles all of the CORS headers automatically for you.

### Sixpack Web Interface

The web interface is deployed behind an Nginx Proxy.

#### Authentication

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
