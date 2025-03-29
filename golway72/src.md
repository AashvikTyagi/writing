# A Conway's Game of Life Demo
<video controls autoplay loop><source src="assets/display.webm" type="video/webm"></video>

Mathematician John Horton Conway's Game of Life is a cellular automaton designed by him in 1970, featuring populated and dead cells on an infinite 2d square grid. Each 'tick', the state of a cell changes depending on the number of neighbours it had in the previous tick, simulating life in a community.  
The specific conditions are:
| neigh  | state |
|--------|-------|
| <2     | dies  |
| 2 or 3 | lives |
| ≥4     | dies  |
| 3      | born  |


I've been interested in the Game of Life since I first read about it, and thought it fairly easy to implement in software. So, using a display and 328p clone board I [had](/#led-matrix-touch) from a previous [project](/#qlock), I made a small desk trinket of sorts to 'mire.

Written in C (I used PlatformIO), it begins with a random state and resets every minute. Per delayed tick, carries out a very simple frame update, storing previous and current cell values. It treats the edges of the display as 'stitched' to the opposite edge ([para 5](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life#Algorithms))&mdash; that is, to look for the cell to the right of the rightmost cell, it checks the leftmost cell in that row. This is done by simply using the remainder after dividing by matrix dimensions, and is more accurate than assuming unshown cells to be dead.

Given that it starts from a (pseudo-)random state, it's interesting how often it happens to generate well-documented, [known patterns](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life#Examples_of_patterns)! For example, here's an infinite [glider](https://en.wikipedia.org/wiki/Glider_(Conway%27s_Game_of_Life)):

<img src="assets/glider.webp" alt="glider pattern on led display" class="two">
<img src="assets/oscillator.webp" alt="oscillating pattern on display" class="two">

Creating this small project was, naturally, a trivial exercise for one of such advanced technical prowess, and the satisfaction derived from observing it is, in the most understated sense, quite delightful.

![name of display written in pen](assets/name.webp)