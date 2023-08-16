---
layout: default
title: Contact Us
nav_order: 11
---

# Contact Us

Please provide your contact details below:

## Contact Details

Name: <input type="text" id="name">
GitHub Handle: <input type="text" id="github">
Email: <input type="text" id="email">

## Message
<textarea id="message" rows="4" cols="50"></textarea>

<button onclick="submitIssue()">Submit</button>

<script>
function submitIssue() {
  var name = document.getElementById('name').value;
  var github = document.getElementById('github').value;
  var email = document.getElementById('email').value;
  var message = document.getElementById('message').value;

  var title = github ? 'Contact Request from @' + github : 'Contact Request from Anonymous';
  var body = '## Contact Details\n\nName: ' + name + '\nGitHub Handle: ' + github + '\nEmail: ' + email + '\n\n## Message\n' + message;

  window.location.href = 'https://github.com/projectvastra/projectvastra.github.io/issues/new?title=' + encodeURIComponent(title) + '&body=' + encodeURIComponent(body);
}
</script>

