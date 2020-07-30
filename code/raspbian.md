# Raspbian

On a fresh install, here's some things you like to do:

```sh
sudo apt-get update -y
sudo apt-get install vim silversearcher-ag
```

Don't bother with Atom at the moment; it's too much effort for most of the work you do on Raspbian.

## Installing RabbitMQ

Using the Volttron script currently fails, due to issues with `erlang-nox`. So, don't bother running this from [here](https://github.com/VOLTTRON/volttron/tree/develop):

