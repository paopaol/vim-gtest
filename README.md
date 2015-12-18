# vim-gtest

**Vim plugin to run *GoogleTest* using https://github.com/benmills/vimux**

<img src="http://files.pezzato.net/github/vim-gtest.gif" />

### Select gtest command

```
:GTestCmd path/to/test/executable
```

### Select tests by name

You can select test cases and test name, with autocompletion.

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

### Run test under cursor

```
:GTestRunUnderCursor
```

## Shortcuts

You can map these commands to your favorite shortcuts:

```
nnoremap <leader>tt :GTestRun<CR>
nnoremap <leader>tu :GTestRunUnderCursor<CR>
nnoremap <leader>tc :GTestCase<space>
nnoremap <leader>tn :GTestName<space>
```
