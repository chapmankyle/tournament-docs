# Scheduler Guideline

A scheduler for the Fail-Safe Cloud Tournament Engine (FSCTE) can be written 
and will be used to schedule matches between players in a tournament. However, 
there is not complete freedom in how the scheduler can be written, and this 
document serves as a guideline for anybody attempting to create a scheduler.

## Language

First things first, the scheduler **must** be written in 
[Go](https://golang.org/) because the backend code for everything related to 
tournament matches is written in Go. 

## Structure

This section describes how the file structure should be laid out.

### Package
As with all Go files, the first line must include the package name, so the 
first line should look like the following:

```Go
package main
```
The above line allows the methods inside of the scheduler to be accessible to 
all other Go files.

### Methods
There is only one required method that needs to be exported, namely `Schedule`. 
However, this method will need to use the following structures (they are 
immediately available and don't need to be declared in the scheduler file since 
the file is a part of the `main` package):

```Go
type Player struct {
	name  string
	score float64
}
```
The above structure contains the name of the player, `name`, and the score 
after a match has completed, `score`. The score can either be `0`, denoting a 
loss, `0.5` denoting a draw or `1` denoting a win.

```Go
type Match struct {
	id      int
	players []Player
}
```
The above structure contains the id of the match, `id`, and a slice of the 
players that will play against each other.

```Go
func Schedule(tournamentName string, players []Player) []Match {
	// schedules matches between `players` in tournament `tournamentName`
}
```
The above method **takes in** the name of the tournament, `tournamentName`, 
and the players in the tournament, `players`. The method then **returns** a 
slice of matches that need to be played. The names of the parameters are free 
to be whatever the file creator wishes, however the data structures used must 
be the same as above.

## Other

The file name can be anything as long as it ends with `.go` and any other 
variables, structures, imports, methods etc. can be used as the file creator 
wishes. 

