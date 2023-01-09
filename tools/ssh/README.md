# SSH

## Authenticate with Key

```sh
# Generate a new key on client
ssh-keygen

# Copy key to server (Linux client)
ssh-copy-id -i .ssh/id_rsa.pub user@remote-host


# Copy key to server (Windows client)
cd c:\Users\username
type .ssh\id_rsa.pub | ssh user@remote-host "cat >> .ssh/authorized_keys"

```

## Port Forwarding using SSH Jump Host
```sh
# Port forward port 3389 from 192.168.1.111 to localhost port 33389 using SSH server user@remote-host
ssh -N user@remote-host -L 33389:192.168.1.111:3389

```