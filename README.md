# Project 7 - WordPress Pentesting

Time spent: 8 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

# 1. CVE-2015-5622 - Cross-Site Scripting
  - [ ] Summary: Once a user's comment is authenticated by the admin, the user can then insert XSS via the reply box.
    - Vulnerability types: Cross Site Scripting
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: 
  <img src="https://github.com/leveewasbry/WordPress-PT/blob/master/giphy.gif" width="200">
  - [ ] Steps to recreate: <br />
	1. Post a comment and wait for Admin's approval.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/XSS/Screen%20Shot%202019-10-31%20at%209.37.59%20PM.png" width="800">
	2. Once authenticated, user can then insert XSS into a reply that will execute upon loading the page.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/XSS/Screen%20Shot%202019-10-31%20at%209.49.35%20PM.png" width="800">
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/XSS/Screen%20Shot%202019-10-31%20at%209.57.17%20PM.png" width="800">
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/changeset/33359) <br /><br />
 
    

# 2. CVE-2017-9061 - Error in Upload when file's too large
  - [ ] Summary: A XSS vulnerability exists when attempting to upload very large files, because the error message does not properly restrict presentation of the filename.
    - Vulnerability types: Cross Site Scripting
    - Tested in version: 4.7.2
    - Fixed in version: 4.7.5
  - [ ] GIF Walkthrough: : 
  <img src="https://github.com/leveewasbry/WordPress-PT/blob/master/giphy.gif" width="200">
  - [ ] Steps to recreate: <br />
	1. Create a large dummy file in terminal.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/File%20too%20large/Screen%20Shot%202019-11-08%20at%2012.26.35%20AM.png" width="800">
	2. Rename the file as a picture and insert the script before the extension.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/File%20too%20large/Screen%20Shot%202019-11-08%20at%2012.24.07%20AM.png" width="800">
	3. Open your browser to http://wpdistillery.vm/wp-admin/media-new.php and upload the file.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/File%20too%20large/Screen%20Shot%202019-11-08%20at%2012.24.14%20AM.png" width="800">
  - [ ] Affected source code:
    - [Link 1]( https://hackerone.com/reports/203515) <br /><br />
    
    

# 3. CVE-2018-6390 - Denial Of Service Overflow
  - [ ] Summary: Exploiting a flaw in WordPress's loading script causes a denial of service by overloading the website with requests.
    - Vulnerability types: Denial of Service Overflow
    - Tested in version: 4.2
    - Fixed in version: 4.9.3
  - [ ] GIF Walkthrough: 
  <img src="https://github.com/leveewasbry/WordPress-PT/blob/master/giphy.gif" width="200">
  - [ ] Steps to recreate: <br />
	1. Retrieve doser.py script from the GitHub repository: https://github.com/quitten/doser.py
	2. Open terminal and execute the script to flood WPDistillery.vm with GET requests.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/DOS/Screen%20Shot%202019-11-07%20at%207.19.37%20PM.png" width="800">
	3. WPDistillery.vm fails to load due to the Denial of Service attack. Only upon shutting down the VM and restarting 		will the page be accessible.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/DOS/Screen%20Shot%202019-11-07%20at%207.19.07%20PM.png" width="800">
  - [ ] Affected source code:
    - [Link 1]( https://www.exploit-db.com/exploits/43968) <br /><br />
    


# 4. (Optional) CVE 2015-5714 - Shortcode Tags
  - [ ] Summary: Allows for injection of arbitrary web script or HTML by leveraging the mishandling of unclosed HTML elements during processing of shortcode tags.
    - Vulnerability types: Cross Site Scripting
    - Tested in version: 4.2
    - Fixed in version: 4.3.1
  - [ ] GIF Walkthrough:
  <img src="https://github.com/leveewasbry/WordPress-PT/blob/master/giphy.gif" width="200">
  - [ ] Steps to recreate: <br />
	1. Create a new post in Text mode.
	2. Insert a malicious script and post.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/DOS/Screen%20Shot%202019-11-07%20at%207.19.07%20PM.png" width="800">
	3. The code will pop up when a user hovers over.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/Shortcode%20Tags/Screen%20Shot%202019-11-07%20at%2011.21.42%20PM.png" width="800">
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/Shortcode%20Tags/Screen%20Shot%202019-11-07%20at%2011.21.49%20PM.png" width="800">
  - [ ] Affected source code:
    - [Link 1]( https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8) <br /><br />
    
  
    
# 5. (Optional) CVE 2017-6817 - Authenticated XSS in Youtube URL Embeds
  - [ ] Summary: Authenticated XSS can be inserted into a YouTube URL embed code.
    - Vulnerability types: Cross Site Scripting
    - Tested in version: 4.2
    - Fixed in version: 4.7.3
  - [ ] GIF Walkthrough: 
  <img src="https://github.com/leveewasbry/WordPress-PT/blob/master/giphy.gif" width="200">
  - [ ] Steps to recreate: <br />
	1. In a post or comment, paste a YouTube URL with an embed code.
	[embed src='https://www.youtube.com/embed/du-TY1GUFGk'][/embed] <br />
	2. Insert an XSS script before before the end of the code.
	[embed src='https://www.youtube.com/embed/du-TY1GUFGk\x3csvg onload=alert("hax")\x3e'][/embed]
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/Youtube%20Embeds/Screen%20Shot%202019-11-07%20at%2010.07.45%20PM.png" width="800">
	3. The script will load when viewing the post.
	<img src="https://github.com/leveewasbry/WordPress-PT/blob/master/WP%20Github%20writeup/Youtube%20Embeds/Screen%20Shot%202019-11-07%20at%2010.08.22%20PM.png" width="800">
  - [ ] Affected source code:
    - [Link 1]( https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8) 

## Assets

https://github.com/quitten/doser.py

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [Exploit Database](https://www.exploit-db.com/exploits/)


## License

    Copyright [1999] [yis]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
