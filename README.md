# FastProgressBar

Simplified wrapper for the no longer updated library at https://code.google.com/p/python-progressbar.
The original project seems to have been continued by a different author at https://github.com/WoLpH/python-progressbar.

The majority of this code was ported from the discontinued https://code.google.com/p/python-progressbar. The full version or the continued GitHub version both are far more feature-rich than this wrapper, which has one configuration. However, for processing jobs that perform repetitive operations many times, I've found the features I have chosen to be the optimal arrangement, and having the features pre-built in the package shortens the text length required to implement them.

## Layout
To make usage faster (I just want a simple progress bar for scripts, not to have to select widgets), the layout of the progressbar is standardized to be:

`Title [optional in title: count] | Percentage | Bar | ETA`

## Usage

To make:   `pbar = progressbar("Title", maxCount)` - parses at most one instance of `&count&` to appear like `12 of 16`.
           
To start:  `pbar.start()`

To update: `pbar.update(currentCount)`

To finish: `pbar.finish()`

When run, looks like:

`Rendering 32 of 33 frames: 99% [################################ ] ETA: 0:00:03`

Automatically adjusts to fill terminal window.

## Importing in a program

Place "FastProgressBar" folder in directory of file using it. Import with:

```python
from FastProgressBar import progressbar 
```

Use as above.

## Example
Included in `__init__.py` in the `if __name__ == '__main__'` section:
```python
import time
from FastProgressBar import progressbar
# Demonstrate
pbar = progressbar("Demonstrating. &count& complete.", 100)
pbar.start()
for i in range(100):
    time.sleep(0.05)
    pbar.update(i)
pbar.finish()
print "Done!"
```
