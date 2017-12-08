# SSH2 Shell Server Examples
## Try out different types of shell servers.

#### To use any of these examples, you will need to generate host keys for the server.

To generate host keys in the examples directory in a unix-like environment:
```
# create a directory for our test keys
mkdir test_keys
cd test_keys
# generate the keys
ssh-kegen -f test_key -C ""
```

# README Example
This is the source code shown in [ssh2-shell-server's README](https://github.com/kstafford3/ssh2-shell-server/blob/mater/README.md)

Connect to the server with an ssh client to recieve a message. The server will then terminate the connection.

## Password Example
### Authenticate with a shared secret.
Provide a method that verifies the user-provided `username` and `password` credentials before they can connect.

We provide an example `checkPassword(username, password)` to get you started. (The password is *password*)

## Public Key Example
### Authenticate with a public key.
To use this method, you must make your public key available as the environment variable `$USER_PUBLIC_KEY`.

Provide two methods to validate and verify public keys.

**Validation** takes in the user-provided username and raw public key and asserts that the server will accept it.

**Verification** takes in the username, a verifier determined by the user's key, and the signature provided by the user.

We provide an example implementation that validates and verifies the login based on `process.env.USER_PUBLIC_KEY`.

## The Echo Shell
The password and public key examples rely on the shell defined in echo-shell.js to manage interactions with a connected client. The echo shell will 'echo' back anything sent to the server, as well as logging it locally.