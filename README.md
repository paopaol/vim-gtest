# vim-gtest

**Vim plugin to quickly select and run
[*GoogleTest*](https://github.com/google/googletest) asyncronously.**

[![asciicast](https://asciinema.org/a/8b6692o60nhtys41jpqpgvopi.png)](https://asciinema.org/a/8b6692o60nhtys41jpqpgvopi)

## Usage

### Select gtest command

```
:GTestCmd path/to/test/executable
```

Or add this line to your `.vimrc`:

```
let g:gtest#gtest_command = "path/to/test/executable"
```

Default is: ./test

### Select tests by name

You can select test case and test name, with autocompletion.

```
:GTestCase MyTestCase
:GTestName MyTestName
```

### Run selected tests

```
:GTestRun
```

### Find tests

Go to the prev/next test in the current buffer.

```
:GTestPrev
:GTestNext
```

### Enable/Disable tests under cursor

This remove/add `DISABLED_` prefix to test name.

```
:GTestToggleEnabled
```

### Insert a new test

This insert a new test under cursor.

```
:GTestNewTest
```

This text will be inserted, with cursor placed on ✎:

```
TEST_F(PreviousFixture, ✎) {
}
```

`PreviousFixture` is the name of the first fixture found backward in the source
code. A fixture is something like this:

```
struct MyTest : public testing::Test {
  ...
}
```

### Run test under cursor

```
:GTestRunUnderCursor
```

### CtrlP

Don't you know what [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim) is?

It's a fantastic fuzzy finder for vim! Try it immediately!

`vim-gtest` extends *ctrlp.vim* with a google test finder. Now you can find
and launch tests at the speed of light!

**Attention:** [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim) must be installed.

### FZF

If you are using [FZF](https://github.com/junegunn/fzf.vim), `vim-gtest` extends *FZF* with a google test finder.
Now you can find and launch tests at the speed of light!

### QuickFix

You can tell `vim-gtest` to highlight failing tests using vim's *QuickFix*. This
is available only when vim is run from `tmux`.

```
:let g:gtest#highlight_failing_tests = 1
:GTestRun
:GTestHighlight
```

If you have [vim-dispatch](https://github.com/tpope/vim-dispatch) installed,
calling `:GTestHighlight` isn't needed.

### Switch files

You can switch from implementation to header to test:

```
:GTestJump
```

By default, filenames must follow this rule:

 - implementation: `src/**/*.cpp`
 - header: `src/**/*.hpp`
 - test: `test/**/*_test.cpp`

Test file suffix can be customized in vimrc using
```
let g:gtest#test_filename_suffix = "Test"
```
GTestJump will then look for test filename
 - test: `test/**/*Test.cpp`

## Shortcuts

You can map these commands to your favorite shortcuts. These are mine:

```
augroup GTest
	autocmd FileType cpp nnoremap <silent> <leader>tt :GTestRun<CR>
	autocmd FileType cpp nnoremap <silent> <leader>tu :GTestRunUnderCursor<CR>
	autocmd FileType cpp nnoremap          <leader>tc :GTestCase<space>
	autocmd FileType cpp nnoremap          <leader>tn :GTestName<space>
	autocmd FileType cpp nnoremap <silent> <leader>te :GTestToggleEnabled<CR>
	autocmd FileType cpp nnoremap <silent> ]T         :GTestNext<CR>
	autocmd FileType cpp nnoremap <silent> [T         :GTestPrev<CR>
	autocmd FileType cpp nnoremap <silent> <leader>tf :CtrlPGTest<CR>
	autocmd FileType cpp nnoremap <silent> <leader>tj :GTestJump<CR>
	autocmd FileType cpp nnoremap          <leader>ti :GTestNewTest<CR>i
augroup END
```

## Development

### Contributing

If you'd like to help, check out the
[issues](https://github.com/alepez/vim-gtest/issues). I'd greatly appreciate
any contribution you make. Beer is also appreciated ☺

If you have a question, a feature request, or a new idea, don't hesitate to
post new issues or pull requests. Collaboration is the most awesome thing in
the open source community!

### Testing

To test this plugin you need to test it with a testable project. `googletest`
can test itself. Testception ☺.

This will download and compile google test and its unit tests:

```
./test/make_test
```

Now from `vim`, just call from command line `:GTestCmd ./test/launch`.

After editing this plugin, just `:source %` and try something. Samples unit
tests can be found in `test/googletest/googletest/samples` directory.

## Thanks

Thanks to the creator of https://github.com/ctrlpvim/ctrlp.vim

Thanks to the creator of https://github.com/fisadev/vim-ctrlp-cmdpalette,
which allowed me to learn how to extend CtrlP.

Special thanks to [Tim Pope](https://github.com/tpope), the author of
[vim-dispatch](https://github.com/tpope/vim-dispatch) and many other useful
plugins.

## Self-Promotion

Like vim-gtest?  Follow the repository on
[GitHub](https://github.com/alepez/vim-gtest) and vote for it on
[vim.org](http://www.vim.org/scripts/script.php?script_id=5292). And if you're
feeling especially charitable, follow [Alessandro Pezzato](http://pezzato.net/)
on [Twitter](http://twitter.com/alepezzato) and
[GitHub](https://github.com/alepez).

If you like the plugin please don't forget to leave a :star: for this project!
This will help me to estimate the plugin popularity and plan further
development.

If you have already starred this repo, thank you!
