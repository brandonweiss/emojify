# Emojify

Converts [emoji aliases][emoji aliases] into emoji. Useful for emojifying `git log` output and the like.

## Requirements

You'll need Ruby. I would've preferred the script to be in Bash but I couldn't figure out how to use `sed` to dynamically replace the aliases. If you have a way to do it I'd love a pull request.

## Installation

### Homebrew

Emojify might be too niche to make it into the main homebrew repo, but you can easily get it from my personal [tap][tap].

```shell
brew tap brandonweiss/homebrew-tap
brew install emojify
```

### Manually

The [`emojify`](bin/emojify) script is self-contained. Just put it somewhere that's in your `$PATH`.

## Usage

### Pipe

```shell
echo ":fish: + :hocho: = :sushi:" | emojify
🐟 + 🔪 = 🍣
```

### File

```shell
emojify where_does_sushi_come_from.txt
🐟 + 🔪 = 🍣
```

### In practice

```text
# .gitconfig
[alias]
  logmoji = !git log | emojify | less -r
```

## Build

I wanted the script to be as portable as possible so it has to be "built".

```shell
bundle install
rake build
```

It uses [gemoji][gemoji] as a data source and embeds a mapping of each emoji alias to emoji character in the script.

[emoji aliases]: http://www.emoji-cheat-sheet.com
[tap]: https://github.com/brandonweiss/homebrew-tap
[gemoji]: https://github.com/github/gemoji

## Contributing

1. Fork it ( http://github.com/brandonweiss/emojify/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am "Add some feature"`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
