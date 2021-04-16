# Installation instructions:

## Clone this repo

mkdir -p ~/socks_ws/src
cd ~/socks_ws/src
git clone git@github.com:JunHaoChng/socks.git
cd ~/socks_ws; source /opt/ros/foxy/setup.bash; colcon build

## Run the example

### In one terminal
cd ~/socks_ws/install/socks/lib/socks
source socks_server
### Open another terminal
cd ~/socks_ws/install/socks/lib/socks
source socks_client
#
## The example's README is at ~/socks_ws/src/socks/include/websocketpp/tutorials/utility_client and /utility_server
