This directory should contain shared credentials for the 'deploy' user on all managed hosts.

The SSH keys should be named 'deploy_id_rsa' for the private key and 'deploy_id_rsa.pub' for the public key.

Run ssh-keygen to generate keys (do NOT set a passphrase). Be careful with the permissions when sharing the
private key with other users (e.g. a CI system).

The sudo password must be in the file 'deploy_password' and must be hashed.

A password hash can be generated using the following command:

mkpasswd --method=SHA-512
