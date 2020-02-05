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


### Second option: add an rcParams file to your path or working directory
This option seems to be good if you want to "forever" alter how your plots look, which could be good for a paper with many figures that you want to all have the same font size, lineweight, e.g., but all might be very different sorts of figures.  

On the other hand, I think the above instructions for writing a style file are good for designing specific situations (e.g. clumped isotope triple plot) or for making a "poster" or "presentation" version of a figure that will have different lineweights, fontsizes, etc. than the paper version.  

Anyway, if you want to (1) add rc params to your current working directory, you should:
1. Copy this example file (https://github.com/matplotlib/matplotlib/blob/master/matplotlibrc.template) into your working directory. You can find the example file in your Anaconda distribution, too. Anyway, once it's in your working directory, any changes there will be applied to any matplotlib activities you do there and not anywhere else.  

As for actually editing this file, there are good instructions in the header, but you want to:
2. Uncomment any lines you want to activate, so an active line should look like
```
lines.markerfacecolor  : pink  ##  sets marker facecolor to pink
```
and not like:
```
# lines.markerfacecolor : pink  ## this is commented so it won't do anything
```
Then, save the file and you should be good to go. When you import matplotlib into your next script (in the working directory), it will throw warnings if any lines in your matplotlibrc file are wrong.  

Note: I think you have to call the file 'matplotlibrc' for python to find it. This is another disadvantage over a style sheet (which you can call anything-you-want.mplstyle).
