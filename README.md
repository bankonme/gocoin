Gocoin is a full bitcoin client solution written in Go language (golang).
At the wallet level, it also supports Litecoin.

The basic components of the software are:

* **downloader** - tool to quickly sync (download) your local blockchain state from the bitcoin p2p network
* **client** - peer-to-peer bitcoin node with an interactive user interface (console or web browser)
* **wallet** - bitcoin/litecoin wallet, designed to be run at off-line PC, for security.

In addition there is also a set of tools, inside the **tools** folder.


# Website
The official web page of the project is served at <a href="http://www.assets-otc.com/gocoin">www.assets-otc.com</a>.

There you can find more documentation, including <a href="http://www.assets-otc.com/gocoin/manual">User Manual</a>.


# Requirements

## Hardware

### Online node
At least 4GB of system memory.

64-bit architecture OS and Go compiler.

File system where you store the database must support files larger than 4GB.

### Offline wallet
The wallet app has very little requirements and should work on any platform with a working Go compiler.

For security reasons, use an encrypted swap file and if you decide to store a password in the `.secret` file,
do it on an encrypted disc.

## Software

### Operating System
The software should work on any OS that has a working Go compiler.
Currently that would be one of the following:

* Windows
* Linux
* OS X
* FreeBSD.

### Additional software

Since no binaries are provided, in order to build Gocoin yourself, you will need the following tools installed in your system:

* **Go** - http://golang.org/doc/install (version 1.2 or higher)
* **Git** - http://git-scm.com/downloads
* **Mercurial** - http://mercurial.selenic.com/

If the tools mentioned above are all properly installed, you should be able to execute `go`, `git` and `hg` from your OS's command prompt without a need to specify a full path to the executables.

Note: Git and Mercurial are only needed for `go get` command to work, which automates installing of the packages.
You can replace `go get` with certain manual steps, in which case you would not need these two tools.
But if you are not familiar with go framework and environment, it is recommended to just have these two tools installed and let `go get` to do the job for you.


# Building

## Download sources
Two extra  packages are needed, that are not included in the default set of Go libraries.
You need to download them, before building Gocoin.
In order to do this (having Mercurial installed in your system), simply execute the following commands:

	go get code.google.com/p/go.crypto/ripemd160
	go get code.google.com/p/snappy-go/snappy

Assuming that you also have Git installed, use `go get` to fetch and install (in the right place, inside your GOPATH) Gocoin sources for you:

	go get github.com/piotrnar/gocoin


Note: if you do not have Mercurial and/or Git installed, you can download the three packages manually, but then make sure to have them extracted
in the right location within your GOPATH folder.

## If you can, have gcc
It is recommended to have gcc complier installed in your system, to get advantage of performance improvements and memory usage optimizations.

For Windows install mingw, or rather mingw64 since the client node needs 64-bit architecture.

### Not having gcc

Not having a compatible gcc installed in your system, trying to build the software, you will likely see an error like this:

	# github.com/piotrnar/gocoin/lib/qdb
	exec: "gcc": executable file not found in %PATH%

You can still compile the problematic package...

To fix the problem just copy file `lib/qdb/no_gcc/membind.go` one folder up (overwriting the original `lib/qdb/membind.go`).

## Compile client
Go to the `client/` folder and execute `go build` there.

## Compile wallet
Go to the `wallet/` folder and execute `go build` there.

## Compile downloader
Go to the `downloader/` folder and execute `go build` there.

## Compile all the tools
Go to the `tools/` folder and execute:

	go build btcversig.go
	go build compressdb.go
	go build fetchbal.go
	go build fetchtx.go
	go build importblocks.go
	go build type2determ.go


# Pull request
I am sorry to inform you that I will not merge in any pull requests.
The reason is that I want to stay the only author of this software and therefore the only holder of the copyrights.
If you are missing some functionality that you'd want in, just describe me what you need and I will see what I can do.
If you want your specific code in though, please fork and develop your own repo.
