Simple Vagrant machine configuration to spin up a development Docker vm.

I was using Docker for Windows, but wanted to run other vm's that weren't working that well on Hyper-V, probably because I don't know how to properly configure it to take full advantage.

Tired of this, and because Hyper-V and VirtualBox don't really go well together, and I don't want to be restarting the computer to switch between the two, I created this to have a close enough experience.

I could have used [Docker Machine](https://github.com/docker/machine), but since the project seems a little bit on the dead side, I just went with Vagrant to configure things.
