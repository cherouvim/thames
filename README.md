# Thames

Thames is a browser and player for the BBC Sound Effects collection which
contains sounds from cafes, markets, cars, typewriters, nature etc.
You can browse the collection online at http://bbcsfx.acropolis.org.uk/.

Thames creates an index for the collection in an sqlite3 database, makes
full text queries to it and downloads and plays the sounds. Each query is an
sqlite3 full text query and is applied verbatim. Usually it is a single term
or a phrase but you can also use NEAR queries.

For the first run, it downloads the index from BBC and creates the database,
so it will be a bit slow. During playback, the sounds are downloaded in the
background so ideally, depending on the sound and download durations, there
will be no delay in playback except for the first sound.

Some examples

play sounds from cafes

```
thames cafe
```

play sounds from cafes and then from typewriters

```
thames cafe typewriter
```

play sounds from cafes and typewriters interleaved

```
thames --shuffle cafe typewriter
```

mix sounds from cafes and typewriters, feel like an author

```
thames --mix cafe typewriter
```

go out in the wild nature

```
thames --mix wind rain water fire
```

browse sounds from space

```
thames --query space
```

## Installation

Thames is tested only with go 1.14 on debian linux, including WSL and crostini.

First you must install `play(1)` with

```
sudo apt-get install sox
```

Then

```
go get github.com/anastasop/thames
```

Thames has a dependency on the sqlite3 driver https://github.com/mattn/go-sqlite3 which is a cgo driver.
If the installation of thames fails then probably you should install the sqlite3 driver manually and then
thames.

### Bugs

- make the sound player configurable
- add a flag to play only cached files
- add more randomness when mixing or interleaving sounds
