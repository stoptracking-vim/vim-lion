lion.vim
========

Lion.vim is a tool for aligning text by some character. It defines some
Vim operators that can be used with motion commands to align a targeted
block of text.

The two operators are `g[` and `g]`. `g[` will add spaces to the left of
the alignment character, and `g]` will add spaces to the right. Both
operators accept a count, a motion, and a single character. Without a
count, all occurrences of the character will be aligned.

For example, `g[ip=` will turn

```php
$i = 5;
$username = 'tommcdo';
$stuff = array(1, 2, 3);
```

into

```php
$i        = 5;
$username = 'tommcdo';
$stuff    = array(1, 2, 3);
```

Typing `3g]i(,` with the cursor somewhere inside `(` and `)` will turn

```php
$names = array(
    'bill', 'samantha', 'ray', 'ronald',
    'mo', 'harry', 'susan', 'ted',
    'timothy', 'bob', 'wolverine', 'cat',
    'lion', 'alfred', 'batman', 'linus',
);
```

into

```php
$names = array(
    'bill',    'samantha', 'ray',       'ronald',
    'mo',      'harry',    'susan',     'ted',
    'timothy', 'bob',      'wolverine', 'cat',
    'lion',    'alfred',   'batman',    'linus',
);
```

It is also possible to align text by a pattern. To enter a pattern, use `/` as
the alignment character (e.g. `glip/`) and then you will be prompted to input
the pattern. To align by `/`, simply leave the pattern empty (by pressing
`Enter`).

Installation
------------

If you don't have a preferred installation method, I recommend
installing [pathogen.vim](https://github.com/tpope/vim-pathogen), and
then simply copy and paste:

```sh
cd ~/.vim/bundle
git clone git://github.com/tommcdo/vim-lion.git
```

Once help tags have been generated, you can view the manual with
`:help lion`.

Options
-------

Option |                Description |                      Default
--- | --- | ---
`g:lion_create_maps`    | Whether to create mappings       | 1
`g:lion_map_right`      | Mapping for right-align operator | g[
`g:lion_map_right_sqz`  | ... and squeeze spaces           | g{
`g:lion_map_left`       | Mapping for left-align operator  | g]
`g:lion_map_left_sqz`   | ... and squeeze spaces           | g}
`b:lion_squeeze_spaces`<br>`g:lion_squeeze_spaces` | Invert default mappings behaviour | `0`

If you hit `g{ip=`, you will turn

```php
$i      = 5;
$user     = 'tommcdo';
$stuff  = array(1, 2, 3);
```
into:
```php
$i     = 5;
$user  = 'tommcdo';
$stuff = array(1, 2, 3);
```
instead of:
```php
$i        = 5;
$user     = 'tommcdo';
$stuff    = array(1, 2, 3);
```
