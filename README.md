# Apollo(v8.0.0) CyberRT

![CyberRT](./docs/CyberRT.gif)

## #1 env

```shell
Ubuntu18
Ubuntu20
```

```shell
sudo apt install libpoco-dev
sudo apt install uuid-dev
sudo apt install libncurses5-dev
sudo apt install python3.6-dev
// Ubuntu18 : python3.6-dev
// Ubuntu20 : python3.9-dev
pip3 install protobuf
```


## #2 build

1. download

```shell
git clone --depth=1 https://github.com/minhanghuang/CyberRT.git
cd CyberRT
```

2. install third party library

> third party(gflag glog fastrtps fastcdr...)

```shell
./scripts/install.sh
```

```shell
source install/setup.bash
```

3. build cyber

```shell
mkdir build && cd build
cmake ..
make -j$(nproc)
```

4. run examples

- pub/sub

> talker

```shell
source setup.bash
./cyber/examples/cyber_example_talker
```
> listener

```shell
source setup.bash
./cyber/examples/cyber_example_listener
```

- component

```shell
source setup.bash
cyber_launch start share/examples/common.launch
./cyber/examples/common_component_example/channel_prediction_writer
./cyber/examples/common_component_example/channel_test_writer
```

## #3 tools

- channel

> list

```
source setup.bash
cyber_channel list

// The number of channels is:  1
// /apollo/test
```

> echo 
```shell
source setup.bash
cyber_channel echo /apollo/test
```
![example](docs/cyber_echo.png)

> more ...

```shell
Commands:
	cyber_channel list	list active channels
	cyber_channel info	print information about active channel
	cyber_channel echo	print messages to screen
	cyber_channel hz	display publishing rate of channel
	cyber_channel bw	display bandwidth used by channel
	cyber_channel type	print channel type
```

- node

```shell
Commands:
	cyber_node list 	List active nodes.
	cyber_node info 	Print node info.
```

- service

```shell
Commands:
	cyber_service list	list active services
	cyber_service info	print information about active service
```

- launch

```shell
cyber_launch start share/examples/common.launch
```

- monitor

```shell
cyber_monitor
```

- recorder

```shell
Commands:
  	cyber_recorder info	Show information of an exist record.
	cyber_recorder play	Play an exist record.
	cyber_recorder record	Record same topic.
	cyber_recorder split	Split an exist record.
	cyber_recorder recover	Recover an exist record.
```

## #4 package

```shell
cmake -DCMAKE_INSTALL_PREFIX=/you/install/path ..
make 
make package
sudo dpkg -i package/*.deb
```

