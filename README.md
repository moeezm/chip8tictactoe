# CHIP-8 Tic-Tac-Toe
This is a challenge I gave myself to code a tictactoe for the CHIP-8 by hand, by which I mean I typed in the opcodes directly with a hex editor

The game works, playing it on some online emulator is easiest: https://ajor.co.uk/chip8/chip8.html

For input, the grid

1 2 3
4 5 6
7 8 9

corresponds to the squares, and pressing 0 will reset the game. It also keeps score which is kinda stupid gameplay wise for a game like tictactoe but it was an additional thing to code so I added it.

The actual code itself is reasonably structured. The biggest mistake I made was wasting all my registers on static information. The CHIP-8 only has one "read/write between memory and registers" command and it reads/writes a contiguous range of k bytes into/from the first k registers. For example, you can't load a specific memory address into an arbitrary register.

So I decided at the beginning to use registers for common information that's static. Certain functions ended up needing to read/write from memory anyways so I had to apply the technique of "dump registers, do stuff, load back registers". Originally I thought doing this would be ugly, but I now think that if I embraced this from the beginning I could've used my registers better. That might've made my code longer, but I'm not sure.
