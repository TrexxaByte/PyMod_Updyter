# -*- coding: utf-8 -*-
#
# ==============================================================================
# Author Email: <joetrex@outlook.com>
# TrexxæByte Technologies™
#
# Copyright© 2022 - See LICENSE file
# Author - Joseph L. Trexler
# 
# ==============================================================================

import os
import subprocess
import sys


# Font color for displaying important info or errors on the terminal display.
RED = '\33[31m'


"""
Attempts to update any outdated Python modules installed on the system. Implementation and
testing for different operating systems has not yet been completed. As of 10/26/2022 project
is less than 24 hours old.
"""
	
# Preemptive attempt to locate the python path for instances in which the terminal doesn't readily 
# recognize 'python' as a viable or acceptable command.
count = 0
py_exe = sys.executable
	
# Accomodation for the possibility sys.executable returns nothing. 
if py_exe == '' or py_exe is None:
	while True:
		py_exe = input('Python path not found! Please enter the path to python.exe: ')
		if os.path.exists(py_exe) is False:
			print('Invalid path. Check the directories and/or dir tree and try again.')
			continue
		elif os.path.isdir(py_exe):
			dir_files = os.listdir(py_exe)
			if 'python.exe' in dir_files:
				py_exe = py_exe + '\\python.exe'
				break
		elif os.path.basename(py_exe) == 'python.exe':
			break
		else:
			print('Unable to locate python.exe from the path you entered. Try searching for python.exe...')
			continue
	
print('Getting list of modules with available version updates. Please wait...')
outdated = subprocess.getoutput(py_exe + ' -m pip list --outdated')
	
# Parse the module name from the rest of the output from pip.
mods = outdated.split('\n')
for mod in mods:
	mods[mods.index(mod)] = mod[0:mod.find(' ')]
print('Module list complete. Beginning update process...')
	
# Run through the list of modules and attempt to upgrade each to the latest version.
for mod in mods:
	subprocess.run(py_exe + ' -m pip install ' + mod + ' --upgrade')
	print(f'{mod} DONE. CHECKING NEXT MODULE...')
	count += 1
	
# Display message to inform user the updating process has finished.
print('All Python module updates/upgrades are complete. A total of ' + str(count) + 
' modules have been updated (or attempted and failed - see pip output messages for errors.')
	

	
	
				
	
		
	
	
	
	
