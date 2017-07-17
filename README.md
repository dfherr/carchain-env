# Setup

### Install Docker

To use this project environment you need to install docker and crane.

`https://docs.docker.com/engine/installation/#supported-platforms`

For ubuntu you can go directly to: `https://docs.docker.com/engine/installation/linux/ubuntu/`

Also follow the post install steps for the docker user and auto start of docker `https://docs.docker.com/engine/installation/linux/linux-postinstall/`

### Install crane

Then install crane `https://www.craneup.tech/docs#installation`

### Setup project

First clone this repository.

Then inside this repository clone the [Carchain](https://github.com/blc-psi/carchain) project. (Do not change the name. The subfolder should be named carchain)

Optionally add `blc-psi-env/bin` to your path, for shortened startup commands.

# Usage

Working with the project is easy. While inside the `blc-psi-env` folder, simply use `crane run carchain` or simply `carchain` if you added the bin to your path.

If you need to run special tasks, such as rake, simply append them: `crane run carchain bundle exec rake -T`

Your local projecct and the code used in the docker container are mirroed for development, so you can immediately see your changes without rebuilding the image or even restarting the docker container.



## Connect nodes:

Run:

```
curl --data '{"jsonrpc":"2.0","method":"parity_enode","params":[],"id":0}' -H "Content-Type: application/json" -X POST localhost:8545
```

Add the "result" to node 1 (replace enode://RESULT in the command):

```
curl --data '{"jsonrpc":"2.0","method":"parity_addReservedPeer","params":["enode://RESULT"],"id":0}' -H "Content-Type: application/json" -X POST localhost:8546
```
