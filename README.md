# ICP AZLE BASED BACKEND PROJECT BOILERPLATE

## Setup instructions

1. clone code from this repository.

2. Navigate into the directory with the package.json file using your terminal.

3. Enter this command in your terminal:

```bash
    nvm use 20 (Uses node version 20)
```

4. Ensure that you have installed podman. This depends on the kind of OS you are using so (Click here to go to the documentation site)[https://podman.io/docs/installation]

5. Ensure that you install dfx virtual machine. You can use this command in your terminal:

    - To install:
    
    ```bash
    DFX_VERSION=0.16.1 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"
    ```

    - To add dfx into the path (If during installation, the path to dfx vm has been set then you can skip this part.):
    
    ```bash
    echo 'export PATH="$PATH:$HOME/bin"' >> "$HOME/.bashrc"
    ```

    - Restart the terminal and test whether dfx has been installed using this command:
    
    ```bash
    dfx --version
    ```

6. Use this command in your terminal to install the dependencies:

```bash
npm install
```

## Start the program

1. To start the local icp, use this command below (Use --clean flag to clean resources before restart):

```bash
dfx start --background --host 127.0.0.1:8000
```

2. To deploy the canister(s), use this command:

```bash
dfx deploy
```

3. To stop the application:

```bash
dfx stop
```

## Interact with the program

1. interacting commands:
	- To create a new message:
    
    ```bash
    curl -X POST http://canister_id.localhost:8000/messages -H "Content-type: application/json" -d '{"title": "todo list", "body": "some important things", "attachmentURL": "url/path/to/some/photo/attachment"}'
    ```

	- To read a single message:
    
    ```bash
    curl http://canister_id.localhost:8000/messages/message_id
    ```

	- To update a message:
    
    ```bash
    curl -X PUT http://canister_id.localhost:8000/messages/message_id -H "Content-type: application/json" -d '{"title": "UPDATED TITLE", "body": "some important things", "attachmentURL": "url/path/to/some/photo/attachment"}'
    ```

	- To read all messages:
    
    ```bash
    curl http://canister_id.localhost:8000/messages
    ```

	- To delete a message:
    
    ```bash
    curl -X DELETE http://canister_id.localhost:8000/messages/message_id
    ```

## Common issues

This is a list of issues you may encounter and how to solve them. I'll update it as I receive more issues.

### Issue 1.0:

error while loading shared libraries: libunwind.so.8: cannot open shared object file: No such file or directory

#### Solution:

Install the libunwind8 library. You may use this terminal command if you're using Ubuntu/Debian based systems:

```bash
sudo apt-get update
sudo apt-get install libunwind8
```
