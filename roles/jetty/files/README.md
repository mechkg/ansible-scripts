This role configures jetty to listen on localhost (127.0.0.1) only.

It is meant to be proxied via nginx to avoid running it as root. SSL is handled by
nginx.

Java heap flags can be edited, but DO NOT remove the "-Djetty.host=127.0.0.1" part
as that will open a MASSIVE security hole on servers without strict firewall policy
(e.g. Ubuntu).
