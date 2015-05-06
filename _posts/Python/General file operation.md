title: "General file operation"
date: 2015-04-18 12:27:27
tags: [python]
categories: [python,junior]
---

```
## show parameter or method
dir("")

## argv number and value
import sys
len(sys.argv) //count
for i in sys.argv: //list

## list all file in dir
from os import listdir
print listdir(".")

## check file exists
if os.path.exists(file_name):

## look for fileName
import os
from os import walk
for (root, dirs, files) in walk("/Users/soeasyright"):
	for file in files:
		if file.endswith('.py'):
			print(os.path.join(root, file))

## Rename FileName 
os.rename(fullpath, fullpath.replace('E', 'e'))

## open file 
-- type1 --
with open(file_name) as f: //no needs file.close

-- type2 --
wopen = open(file_name,'w')  //w,w+
wopen.write(tmp_word)
wopen.close()

## try except
try:
	print 'deal something'
	raise EOFError('XD')
	print 'ok'
except EOFError as e
	print e.args  ## XD
	type, message, traceback = sys.exc_info()
	print type ##<type 'exceptions.EOFError'>
	print message ##XD
finally:
	print 'finally'	


## exit python
import sys
sys.exit(0) 
sys.exit(1) //something error

```