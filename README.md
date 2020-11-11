# anewer [![@ysfr][twitter-img]][twitter]
anewer appends lines from stdin to a file if they don't already exist in the file. You could also use it as `uniq` wihtout `sort`. This is a rust version of [tomnomnom/anew](https://github.com/tomnomnom/anew). It makes use of [tkaitchuck/aHash](https://github.com/tkaitchuck/aHash) to cut down runtime to ~50%. Since only hashed lines are held in memory, it cuts down memory usage for inputs with long lines.

[twitter-img]:  https://img.shields.io/badge/twitter-@ysfr-blue.svg
[twitter]:      https://twitter.com/ysfr


## Usage

```
$ anewer
USAGE:
    anewer [FLAGS] [filename]

FLAGS:
    -n, --dry-run    Dry run, will leave the file as it is
    -h, --help       Prints help information
    -q, --quiet      Quiet, won't print to stdout
    -V, --version    Prints version information

ARGS:
    <filename>
```

## Installation

```
cargo install anewer
```

#### Add unknown elements of newthings.txt to things.txt
```
$ cat things.txt
Zero
One
Two

$ cat newthings.txt
One
Two
Three
Four

$ cat newthings.txt | anewer things.txt
Three
Four

$ cat things.txt
Zero
One
Two
Three
Four
```

#### Or use it as simple uniq without sort
```
$ cat list.txt
One
One
Two
Two
Three
Four
Three
Four

$ cat list.txt | anewer
One
Two
Three
Four
```

# License
GPLv3+
