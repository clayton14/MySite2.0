# Clayton's Site2.0

This is the repo for my [website](https://claytoneasley.org/).
You can find all of my projects, ideas, thoughts and other random things here  😁.

## Preview from source

If you want to test out the site on your computer then, here is what you need to do:

1. Make sure you have the [GO](https://go.dev/) programing language and [Hugo](https://gohugo.io/) installed on your machine:
   
    - Arch Linux:
        ```bash
        sudo pacman -S --needed go
        sudo pacman -S --needed hugo
        ```
    - Debian:
        ```bash
        sudo apt install go
        sudo apt install hugo
        ```
    - If you're running another distribution, then use your package manager.
 
2. Run these commands:You should be able to find both of these dependencies on your distributions package manager respectively.
    ```bash
    git clone https://github.com/clayton14/MySite2.0.git
    cd MySite2.0/src
    hugo server
    ```
6. Open `http://localhost:1313` in your web browser


## Contributing
Want to contribute? Read [the contributing guide](/CONTRIBUTING.md).
 

### Where is version 1.0?
In short, I was writing my old website in raw HTML, CSS an JS. This process was taking too long, so I switched to using [Hugo](https://gohugo.io/) to speed up the process. If you want to see the old site (you don't), then you can view the archived repo [here](https://github.com/clayton14/MySite).