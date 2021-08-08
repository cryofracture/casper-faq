# Casper Operators FAQ
--------------------------------------------------
## What operating systems can I run a casper node with?
Casper is currently only tested and packaged for Ubuntu 18.04 or 20.04.

## What ports are required for casper-node?
* 35000 (required to be externally visible)

* 7777 RPC endpoint for interaction with casper-client

* 8888 REST endpoint for status and metrics (having this accessible allows your node to be part of network status)

* 9999 SSE endpoint for event stream.

## What are the recommended system specs for a casper node?
* 4 Cores
* 32 GB Ram
* 1 TB disk (Both SSDs and HDDs work, but SSDs perform initial sync much faster.)
* Linux machine running Ubuntu 18.04 or 20.04 with a Rust build environment

## How do I check my node’s status?
nce your node is running, you can run query your node's status port and look for the .last_added_block_info to confirm a node's synchronization status. The output will look similar to:

```
curl -s http://localhost:8888/status | jq .last_added_block_info
{
"hash": "73f398f89dfe2b980634281c0d6be8379b27aedbf4029f699219fafa1e09526c",
"timestamp": "2021-07-09T04:56:42.240Z",
"era_id": 1090,
"height": 106926,
"state_root_hash": "5e7bd420cb5d3290cf50036ada510c9c1adcf63198381c398403086f739394c8",
"creator": "011752f095ee6d2902540ea4fafd649da4b7b0c2a6e38176fb7f661a0e463d43b4"
}
```

## If I am not running a node locally, what --node-address do I use for making requests? 
You can see the IP address of other nodes on the network by visiting the block explorder, cspr.live, specifically the peers section, [here](https://cspr.live/tools/peers). Node operators can restrict access to 7777, 8888, and 9999 to not respond to external requests. You should try multiple addresses from this page.

## Do I have to run a node 24/7?
To operate a node as a validator, your node has to be online 24/7, otherwise, you will be ejected for liveness failure and lose rewards. If you can't run a node 24/7, you can delegate your tokens to a validator with a healthy node and a good uptime.