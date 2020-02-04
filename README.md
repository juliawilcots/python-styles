# python-styles
Custom python style files designed by me

### (Very basic instructions) to add a matplotlib style file:
(Instructions from https://matplotlib.org/tutorials/introductory/customizing.html)
1. Find the path to your matplotlib configuration directory:
  ```
  $ python
  >>> import matplotlib as mpl
  >>> mpl.get_configdir() 
  ```
2. If there is no 'stylelib' directory in your mpl_configdir, add it:
```
~/.matplotlib$ mkdir stylelib
$ cd stylelib
```
3. And then write your style file, saving with the extension ```.mplstyle```
```
$ vim [your style file's name].mplstyle
```
(To start writing in vim, press 'i' (for "INSERT"). Once you're done writing, press 'esc', then type ':wq' and press 'return')
 
If any of the above steps do not work, you can try to find the ```core.py``` file (in my Anaconda distribution, at least), which should have lines that look something like:
```
# Users may want multiple library paths, so store a list of paths.
USER_LIBRARY_PATHS = [os.path.join(mpl.get_configdir(), 'stylelib')]
STYLE_EXTENSION = 'mplstyle'
STYLE_FILE_PATTERN = re.compile(r'([\S]+).%s$' % STYLE_EXTENSION)
```
If your mpl configdir is wonky or you have changed your paths at some point, these few lines of code should help you figure out where to write your style files. (You want USER_LIBRARY_PATHS to point to them!)
