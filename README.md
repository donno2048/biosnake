# Biosnake

I use my [COM-BIOS integration program](https://github.com/donno2048/combios) to embed my [snake game](https://github.com/donno2048/snake) into a playable BIOS.

Compile `snake.raw` by running:

```sh
git submodule update --init                                    # checkout the submodules
nasm snake/snake.asm -o snake.com                              # compile the snake game
nasm combios/bios.asm -D COM=snake.com -I combios -o snake.raw # compile the snake bios
rm snake.com                                                   # remove the snake game com file
```

You can use qemu to emulate running the BIOS:

```sh
qemu-system-i386 -display curses -bios snake.raw -icount 19,align=on
```

Use your numpad arrow keys to control the snake.
