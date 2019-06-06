# Codex Trunk
Trunk node for between chains

- [Codex Trunk](#codex-trunk)
  - [Introduction](#introduction)
    - [Design](#design)
    - [Types](#types)
    - [Governance](#governance)
  - [Installation](#installation)
  - [Config](#config)


## Introduction

Trunk is part of the Codex muit-chain system. 
Some trunk node provides a decentralized state synchronization channel between the two chains. 
In particular, all chains in codex muit-chain system will have a channel by trunk nodes to codex.relay chain, so every chains can share their state to others by this.

### Design

The CODEX relay chain provides relay services between the chains. 
In the CODEX multi-chain system, chains and chains do not directly interact with each other, but through the CODEX relay chain. 
For hide the different between chains in the process of cross-chain, we add a 'relay layer' called `trunk`.
`Trunk` can provide a state transmission channel between any two chains.

Different chains often have different governance structures and economic models,  
So the channel in the symmetrical direction will not be equal.

### Types

Support two chains called A and B, there are three types of trunk nodes: Committer, Watcher, and Checker,

- **Committer** : commit chain A block to B
- **Watcher** : commit chain B state change to A
- **Checker** : check committers and watchers

Committer can send block to other chain:

![committer](doc/pic5.png)

Watcher can handler state change from other chain:

![watcher](doc/pic6.png)


### Governance

Nodes in trunks need build governance way. 

TODO: some examples

## Installation

First build the trunk

```bash
go get -u -v github.com/codexnetwork/trunk
cd $GOPATH/src/github.com/codexnetwork/trunk
go get -v ./...
go install
```

You can use `-h` to get params for trunk:

```
trunk -h
Usage of ./trunk:
  -cfg string
    	config file path (default "./config.json")
  -d	run in debug mode
```

After make a config, can start trunk by:

```bash
trunk -cfg /path/to/config.json
```

## Config