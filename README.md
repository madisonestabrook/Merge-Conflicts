  Most of the time, Git will successfully merge branches together without any problems.
  However, there are times in which a merge cannot be fully performed. <em>A merge
  conflict is when a merge fails.</em> If a merge conflict occurs, Git will try to
  combine as much as it can, but it will leave special markers, such as
  <strong><span style="color: #808080;">&gt;&gt;</span></strong> and <strong><span style=
  "color: #808080;">&gt;&gt;</span></strong>, that tell us (the programmers!) what we
  need to fix. This article:

  <ul>
    <li><a href="#causes">Addresses what causes a merge conflict</a></li>
    <li><a href="#instructions">Provides a 5-part instructions on creating a merge
    conflict</a></li>
    <li><a href="#explanation">Explains the output of merge conflict</a></li>
    <li><a href="#resolution">Demonstrates how to resolve a merge conflict</a></li>
  </ul>

  <h2 id="causes">What Causes a Merge Conflict?</h2>Git tracks lines in files. <em>A
  merge conflict occurs when the exact same line or lines are changed in separate
  branches</em>. For example, if we are on a <span style=
  "color: #808080;"><strong>alter-sidebar-style</strong></span> branch and change the
  sidebar&rsquo;s heading to &ldquo;About Me&rdquo; but, then, on a different branch,
  change the sidebar&rsquo;s heading to &ldquo;Information About Me,&rdquo; which heading
  should Git choose? The heading is changed on both branches; Git does not know which
  change to keep. We will force a merge conflict, which teaches us how to resolve it.
  Remember a merge conflict occurs when the exact same line or lines are changed in
  separate branches. All we need to do is edit the exact same line on 2 different
  branches and try to merge them.

  <h2 class="instructions">Forcing a Merge Conflict Instructions</h2>Again, remember a
  merge conflict occurs when the exact same line or lines are changed in separate
  branches. Our plan is as follows:

  <ol>
    <li><a href="#branch1Change">Change the heading on the <strong><span style=
    "color: #808080;">master</span></strong> branch</a></li>
    <li><a href="#branch2Change">Create a <strong><span style=
    "color: #808080;">heading-update</span></strong> branch that is located on the commit
    before the recently modified master branch</a></li>
    <li><a href="#branch2Change">Change the same heading</a></li>
    <li><a href="#branch2Change">Switch back to the <span style=
    "color: #808080;"><strong>master</strong></span> branch</a></li>
    <li><a href="#branch2Change">Merge the <strong><span style=
    "color: #808080;">heading-update</span></strong> branch</a></li>
  </ol>However, before we we begin, make sure you clone my GitHub gist of this project's
  files, which is found at <a href=
  "https://github.com/madisonestabrook/Merge-Conflicts.git" target="_blank" rel=
  "noopener">https://github.com/madisonestabrook/Merge-Conflicts.git</a>.

  <h3 id="branch1Change">Change Heading on Branch 1 (Step 1)</h3>Since the <span style=
  "color: #808080;"><strong>master</strong></span> branch is a regular branch, just alter
  the heading while we are on <span style=
  "color: #808080;"><strong>master</strong></span> by completing the following steps:

  <ol>
    <li>Using the <strong><span style="color: #808080;">cd</span></strong> command to
    navigate to the new-git-project folder <img class="alignleft wp-image-581 size-full"
    src="http://www.madisonestabrook.com/wp-content/uploads/2018/05/cd_screenshot.png"
    alt=
    "Screenshot of Git Bash on a Windows machine that shows the results of running cd new-git-project"/></li>
    <li>Make sure you are on the <span style=
    "color: #808080;"><strong>master</strong></span> branch by using the
    <strong><span style="color: #808080;">git checkout</span></strong> command
    <img class="alignleft wp-image-583 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_checkout_master_screenshot.png"
    alt=
    "Screenshot of Git Bash on a Windows machine that shows the results of running git checkout master" /></li>
    <li>Change the <span style="color: #808080;"><strong>&lt;h1&gt;</strong></span> to
    something other than what it currently is, such as &ldquo;Quest&rdquo; <img class=
    "alignleft wp-image-585 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/change_h1_screenshot.png"
    alt="Screenshot of index.html with line 13 selected" /></li>
    <li>Save <span style="color: #808080;"><strong>index.html <img class=
    "alignleft wp-image-587 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/save-index.png" alt=
    "Screenshot showing how to save index.html in Visual Studio Code " /></strong></span></li>
    <li>Commit <span style="color: #808080;"><strong>index.html</strong></span> to the
    repository by using <span style="color: #808080;"><strong>git add
    index.html</strong></span> and <strong><strong><span style="color: #808080;">git
    commit <img class="alignleft wp-image-589 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/commit_index.png" alt=
    "Screenshot showing how to commit index.html in Git" /></span></strong></strong></li>
  </ol>

  <h3 id="branch2Change">Change Heading on Branch 2 (Steps 2-5)</h3>Now, we need to
  create a different branch and update its heading. The branch that we create must not
  branch from the main branch. If we make a branch that branches off the main branch,
  that change be considered ahead; Git will use that change instead of the change we just
  made on <span style="color: #808080;"><strong>master</strong></span>. We need to put
  our new branch in the past. To do that, complete the following steps:

  <ol>
    <li>View the previous commit's SHA by using <span style="color: #808080;"><strong>git
    log --oneline <img class="alignleft wp-image-593 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_log_-oneline_output-1.png"
    alt=
    "Screenshot showing the results of running git log --oneline on a Windows machine " />
    </strong></span></li>
    <li>Create <span style="color: #808080;"><strong>heading-update</strong></span> by
    typing <strong><span style="color: #808080;">git branch
    heading-update</span></strong>. <img class="alignleft wp-image-595 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/created_heading-update.png"
    alt=
    "Screenshot showing how to create and the results of creating a new branch" /></li>
    <li>Run <strong><span style="color: #808080;">git log --oneline --decorate --graph
    --all</span></strong> to make sure that the heading-update branch is currently
    checked-out <img class="alignleft wp-image-596 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_log_-oneline_-decorate_-graph_-all_output.png"
    alt=
    "Results of running git log --oneline --decorate --graph --all on a windows machine"
    width="827" height="474" /></li>
    <li>Update the <em>same</em> heading in index.html that you previously updated; the
    content of this heading should be different <img class=
    "alignleft wp-image-598 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/changed_heading_1.png"
    alt="Screenshot of index.html in Visual Studio Code with line 13 highlighted" /></li>
    <li>Save <strong><span style="color: #808080;">index.html</span></strong>.
    <img class="alignleft wp-image-600 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/saved-index.png" alt=
    "Screenshot showing how to save index.html in Visual Studio Code" /></li>
    <li>Commit <span style="color: #808080;"><strong>index.html</strong></span> to the
    repository by using <span style="color: #808080;"><strong>git add
    index.html</strong></span> and <span style="color: #808080;"><strong>git commit
    <img class="alignleft wp-image-601 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/commit_index-1.png" alt=
    "Screenshot showing how to commit index.html in Git Bash on a Windows machine" /></strong></span></li>
    <li>Make sure you are on the master branch by using <strong><span style=
    "color: #808080;">git checkout <img class="alignleft wp-image-602 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_checkout.png" alt=
    "Screenshot that shows the results of running git checkout on a Windows machine using Git Bash" />
    </span></strong></li>
    <li>Merge <span style="color: #808080;"><strong>heading-update</strong></span> by
    running <strong><span style="color: #808080;">git merge heading-update <img class=
    "alignleft wp-image-606 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_merge_heading-update-1.png"
    alt=
    "Screenshot that shows how to run git merge heading-update on a Windows machine using Git Bash" />
    </span></strong></li>
    <li>Verify that you get an error message <img class=
    "alignleft wp-image-607 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/error_message.png" alt=
    "Screenshot of error message in Git Bash on a Windows machine " /></li>
  </ol>

  <h2 class="explanation">Merge Conflict Output Explained</h2>The Terminal's output is:

  <blockquote>
    <pre>
<code class="lang-bash">$ git merge heading-update 
Auto-merging index.html
CONFLICT (content): Merge conflict <span class="hljs-keyword">in</span> index.html
Automatic merge failed; fix conflicts and <span class=
"hljs-keyword">then</span> commit the result.</code>
</pre>
  </blockquote>Notice:

  <ol>
    <li>Right after <span style="color: #808080;"><strong>git merge
    heading-update</strong></span>, Git tries merging the file that was changed on both
    branches, which is <strong><span style="color: #808080;">index.html</span></strong>.
    However, there was a conflict.</li>
    <li>Git tells us what happened and what to do in the last line.</li>
  </ol>Run <span style="color: #808080;"><strong>git status</strong></span> and read its
  output, which says the merge conflict is inside <span style=
  "color: #808080;"><strong>index.html</strong></span>. <img class=
  "alignleft wp-image-609 size-full" src=
  "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_status.png" alt=
  "Screenshot showing the results of running git status " /> Open <strong><span style=
  "color: #808080;">index.html</span></strong> in your preferred code editor. <img class=
  "alignleft wp-image-611 size-full" src=
  "http://www.madisonestabrook.com/wp-content/uploads/2018/05/index_after_commit_fail.png"
  alt="Screenshot showing index.html with error messages" />

  <h3>Explanation of Indicators</h3>

  <table>
    <tbody>
      <tr>
        <td><b>Indicator</b></td>
        <td><b>Explanation</b></td>
      </tr>
      <tr>
        <td><span style="color: #808080;"><strong>&lt;&lt;&lt;&lt;&lt;&lt;&lt;
        HEAD</strong></span></td>
        <td>Everything between this line and the next indicator shows the current
        branch&rsquo;s content.</td>
      </tr>
      <tr>
        <td><span style="color: #808080;"><strong>||||||| merged common
        ancestors</strong></span></td>
        <td>Everything between this line and the next indicator shows the original
        lines.</td>
      </tr>
      <tr>
        <td><strong><span style="color: #808080;">=======</span></strong></td>
        <td>This shows the end of original lines; everything between this line and the
        next indicator shows what is on the branch that is being merged in.</td>
      </tr>
      <tr>
        <td><span style="color: #808080;"><strong>&gt;&gt;&gt;&gt;&gt;&gt;&gt;
        heading-update</strong></span></td>
        <td>This is the ending of what is on the branch that is being merged in. In our
        case, this is the <strong><span style=
        "color: #808080;">heading-update</span></strong> branch.</td>
      </tr>
    </tbody>
  </table>

  <h2 class="#resolution">Resolving a Merge Conflict</h2>Git uses the merge conflict
  indicators to show what caused the conflict on the 2 different branches and what the
  original line used to be. To resolve a merge conflict, complete the following steps:

  <ol>
    <li>Choose which lines or line to keep</li>
    <li>Remove all lines with indicators</li>
    <li>Save the file</li>
    <li>Commit <span style="color: #808080;"><strong>index.html</strong></span> to the
    repository by using <span style="color: #808080;"><strong>git add
    index.html</strong></span> and <span style="color: #808080;"><strong>git commit
    index.html</strong></span></li>
  </ol>

  <h2>Merge Conflict Recap</h2>A merge conflict happens when the lines or line have been
  changed on different branches that are being merged. Git will stop merging to show the
  error. To resolve the conflict in a file, complete the following steps:

  <ol>
    <li>Determine what needs to be kept</li>
    <li>Locate and remove all lines with merge conflict indicators <img class=
    "alignleft wp-image-627 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/edited_index.png" alt=
    "Edited index.html with line 13 highlighted" /></li>
    <li>Save and stage the file or files <img class="alignleft wp-image-629 size-full"
    src="http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_add_index.png"
    alt=
    "Screenshot of Git Bash that shows the results of running git add index.html" /></li>
    <li>Make a commit <img class="alignleft wp-image-630 size-full" src=
    "http://www.madisonestabrook.com/wp-content/uploads/2018/05/git_commit.png" alt=
    "Screenshot showing how to make a commit in Git" /></li>
  </ol>A file can have multiple merge conflicts; be sure to check all the file for merge
  conflicts by searching for <strong><span style=
  "color: #808080;">&lt;&lt;&lt;</span></strong>.
