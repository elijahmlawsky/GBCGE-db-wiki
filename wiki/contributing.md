# How to contribute to this wiki

## Create a github account and join the NBMG organization
1. Create a github user account at (github.com)[github.com]
2. Once you have done so, send an email to eodean@unr.edu with your github username.
3. You will then receive an invite to join the "wiki-collaborators" group within the NBMG github organization. Once you have accepted the invite, you can then contribute.

If you want to contribute but do not want to make a github account, you can send text that you want included in the wiki to eodean@unr.edu.

## How to contribute
1. Go to nbmg-unr.github.io
2. Click "Add new post."
3. This will take you to an editor window on github. Add a file name at the top of the post (no spaces, ex. "test_post.md"). All names must end with the "md" description.
4. Type your content in to the box. All of the content needs to be written in (markdown)[https://www.markdownguide.org/getting-started/]. If you already have a word document that you'd like to post, you can use a (word to markdown converter)[https://word2md.com/].
5. Click on the "preview" tab to make sure the content looks how you want it to look.
6. Add a "commit message" - a description of the content that you are posting.
7. Choose the "commit directly to master branch" option, then press "commit new file."
8. To add your new file to the table of contents, either directly edit the sidebar.html file (https://github.com/NBMG-UNR/NBMG-UNR.github.io/blob/master/_includes/nav/sidebar.html - click on the pencil icon to edit) and add your post under the appropriate section using html. The structure should be as follows:

`<li><a href="{{ '/your_file_name_here.html' | relative_url }}">Your title here</a></li>`

Note that the extension in this link says "html" instead of md.

Alternatively, you can email eodean@unr.edu and ask that a link be added for your file.
