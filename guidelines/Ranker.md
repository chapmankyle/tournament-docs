# Ranker Guideline

A ranker for the Fail-Safe Cloud Tournament Engine (FSCTE) can be written and 
will be used to rank players in all tournaments. However, there is not complete 
freedom in how the ranker can be written, and this document serves as a 
guideline for anybody attempting to create a ranker.

## Language

First things first, the ranker **must** be written in [Go](https://golang.org/) 
because the backend code for everything related to tournament matches is written 
in Go. 

## Structure

This section describes how the file structure should be laid out.

### Package
As with all Go files, the first line must include the package name, so the 
first line should look like the following:

```Go
package main
```
The above line allows the methods inside of the ranker to be accessible to all 
other Go files.

### Methods
There are only two required methods that need to be exported, namely 
`UpdateRating` and `GetInitialRating`.

```Go
func UpdateRating(ratingA, ratingB int, scoreA, scoreB float64) (int, int) {
	// update rating of player A and B based on previous ratings and scores
}
```
The above method **takes in** the ratings of two players, where the current 
rating for player 1 is `ratingA` and the current rating for player 2 is 
`ratingB`, as well as the score for player 1 (`scoreA`) and player 2 (`scoreB`) 
after the match has been played. The method then **returns** the new rating for 
player 1 and player 2. The names of the parameters are free to be whatever the 
file creator wishes, however the data structures used must be the same as above.

```Go
func GetInitialRating() float64 {
	// return initial rating that all players start with
}
```
The above method has no parameters and **returns** the initial rating that all 
players will start with.

## Other

The file name can be anything as long as it ends with `.go` and any other 
variables, structures, imports, methods etc. can be used as the file creator 
wishes.

