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
  var name = document.getElementById('name').value || 'Anonymous';
  var github = document.getElementById('github').value || 'Anonymous';
  var email = document.getElementById('email').value || 'Anonymous';
  var message = document.getElementById('message').value;

  var title = github === 'Anonymous' ? 'Contact Request from Anonymous' : 'Contact Request from @' + github;
  var body = '## Contact Details\n\nName: ' + name + '\nGitHub Handle: ' + github + '\nEmail: ' + email + '\n\n## Message\n' + (message || '*No message provided*');

  if (!message) {
    alert('Please provide a message before submitting.');
    return;
  }

  var encodedTitle = encodeURIComponent(title);
  var encodedBody = encodeURIComponent(body);

  var socialLinks = '
    <div>
      <a href="https://twitter.com/intent/tweet?text=%0A" target="_blank">
        <button>Tweet</button>
      </a>
      <a href="https://www.facebook.com/sharer/sharer.php?u=&title=&quote=" target="_blank">
        <button>Facebook</button>
      </a>
      <a href="https://www.linkedin.com/shareArticle?mini=true&title=&summary=" target="_blank">
        <button>LinkedIn</button>
      </a>
      <a href="https://www.instagram.com/?text=%0A" target="_blank">
        <button>Instagram</button>
      </a>
      <a href="mailto:?subject=&body=" target="_blank">
        <button>Email</button>
      </a>
    </div>
  ';

  var popupContent = '<p>Your contact details have been submitted.</p>' + socialLinks;

  var popup = window.open('', '_blank', 'width=600,height=400');
  popup.document.open();
  popup.document.write(popupContent);
  popup.document.close();
}
</script>

