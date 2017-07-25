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

Optionally add `carchain-env/bin` to your path, for shortened startup commands.

You need to manually add the dev network (for now):

`docker network create --subnet=172.28.0.0/16 --gateway=172.28.0.1 dev`

# Usage

Working with the project is easy. While inside the `carchain-env` folder, simply use `crane run carchain` or simply `carchain` if you added the bin to your path.

If you need to run special tasks, such as rake, simply append them: `crane run carchain bundle exec rake -T`

Your local project and the code used in the docker container are mirroed for development, so you can immediately see your changes without rebuilding the image or even restarting the docker container.

### Cleanup

To force a full update run:

`git pull && crane rm --force carchain && crane rm --force parity && crane rm --force parity-node1 && crane rm --force parity-node2 && crane pull`

From time to time you may want to delete old unused images:

`docker rm $(docker ps -a -q)`

## Comments:

If you're asked for a signer token in parity web ui use:

```
curl --data '{"method":"signer_generateAuthorizationToken","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```

Adjust the port according to the node (`node0 8545`, `node1 8546`, `node2 8547`)

## License

[MIT](https://github.com/blc-psi/carchain-env/blob/master/LICENSE)

Copyright (c) 2017 Dennis-Florian Herr
