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



## Comments:

If you're asked for a signer token in parity web ui use:

```
curl --data '{"method":"signer_generateAuthorizationToken","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```

Adjust the port according to the node (`node0 8545`, `node1 8546`, `node2 8547`)
