# Project 7 - WordPress Pentesting

Time spent: **2.5** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Vulnerability Name or ID: WordPress <= 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: In WordPress, an author or contributor level user can create an alert by entering HTML code surrounded by `<code>` tags when editing or creating a post.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: 
    - ![Alt Text](https://github.com/rlh2ph/CodepathWeek7/blob/master/AuthenticateXSSGif.gif)
  - [ ] Steps to recreate: 
      - Attacker must have either a contributor or author account
      - Create a post with `<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>` surrounded in `<code>` tags
      - Hover the mouse over the link to see the alert pop up
  - [ ] Affected source code:
    - [Link 1](http://wpdistillery.vm/?p=6&preview=true)
2. (Required) Vulnerability Name or ID: WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: Admin inserts adds new media object and intercepts it with burb. Adds script to the media file name to create an alert of the admin's cookie when the media is accessed.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.10
  - [ ] GIF Walkthrough: 
    - ![Alt Text](https://github.com/rlh2ph/CodepathWeek7/blob/master/ImageXSSGif.gif)
  - [ ] Steps to recreate: 
    - Must be an admin and have Burp installed
    - Upload new media
    - Intercept the upload
    - Change file name to `cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg`
    - Access link below to view cookie alert
  - [ ] Affected source code:
    - [Link 2](http://wpdistillery.vm/cengizhansahinsumofpwn/)
3. (Required) Vulnerability Name or ID: WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: This XSS attack creates an alert that says "hello world" and then disbles the admin's access of the site. Nothing can be clicked or interacted with.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: 
    - ![Alt Text](https://github.com/rlh2ph/CodepathWeek7/blob/master/AlertXSSGif.gif)
  - [ ] Steps to recreate: 
    - As a user, create a comment
    - In the body of the comment, paste the following code: `<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>`
    - Replace the `AAAAAAAAAAAA...[64 kb]..AAA` with 64 kb of As. Enough until the browser begins to lag.
    - Post the comment
    - Login as an admin, approve the comment, and visit the post that the comment was on
    - An alert should pop up that reads: "hello world" and functionality on the page should be disabled
  - [ ] Affected source code:
    - [Link 3](http://wpdistillery.vm/hello-world/)
 

## Assets

List any additional assets, such as scripts or files

N/A

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work:

The only challenges during this assignment were figuring out which vulnerabilities to test based on my knowledge of cybersecurity at this point. There were other challenges that seemed intersting to test, such as DOS attacks, but I do not have enough knowledge to perform such an attack.

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
