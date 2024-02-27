# morpho-manual
Manual for the Morpho language

This is a translation of the Morpho manual from the original TeX to an mdBook format.

To build the book, you need to have [`mdbook`](https://github.com/rust-lang/mdBook) installed. You can install it with `cargo`:

```bash
cargo install mdbook
```

Then, you need to generate the figures and the reference section by running the `build.py` script:
```bash
python build.py
```
(Make sure to change the `libmorphofolder` path to your local libmorpho folder in the `build.py` script. In the future, we will auto-download the help from GitHub.)

Finally, you can build the book by running `mdbook`:
```bash
mdbook build
```

This will generate the HTML files in the `book` directory. You can view the book by opening the `index.html` file in your browser.

To preview the book, you can run the following command:
```bash
mdbook serve --open
```

# Contributing

Contributions are absolutely welcome! If you find any errors or have any suggestions, please open an issue or a pull request.
