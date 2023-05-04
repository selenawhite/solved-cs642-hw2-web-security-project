Download Link: https://assignmentchef.com/product/solved-cs642-hw2-web-security-project
<br>
<strong>Web Security Project</strong>

For this project, you are going to use a virtual machine running (an ancient) version of Linux. We provide basic VM images for both Oracle VirtualBox and VMware. CSL Linux machines all have VirtualBox pre-installed.

Download Oracle’s Virtual Box: <strong><u><a href="https://www.virtualbox.org/wiki/Downloads">https://www.virtualbox.or</a></u></strong><strong><a href="https://www.virtualbox.org/wiki/Downloads">g</a><u><a href="https://www.virtualbox.org/wiki/Downloads">/wiki/Downloads</a></u></strong> <strong><a href="https://www.virtualbox.org/wiki/Downloads">(</a><u><a href="https://www.virtualbox.org/wiki/Downloads">https://www.virtualbox.or</a></u><a href="https://www.virtualbox.org/wiki/Downloads">g</a><u><a href="https://www.virtualbox.org/wiki/Downloads">/wiki/Downloads) </a></u></strong>Download

<a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">VMware: </a><strong><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">https://m</a></u></strong><strong><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">y</a><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">.vmware.com/en/web/vmware/free#desktop_end_user_computin</a></u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">g</a><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">/vmware_workstation_pla</a></u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">y</a><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">er/12_0</a></u></strong>

<strong><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">(https://m</a></u></strong><strong><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">y</a><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">.vmware.com/en/web/vmware/free#desktop_end_user_computin</a></u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">g</a><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">/vmware_workstation_pla</a></u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">y</a><u><a href="https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/12_0">er/12_0)</a></u></strong>

VMware is only available free on Linux and Windows; if you have VMware fusion for Mac that may work as well.

Environment Setup

Download the BoxesX <strong><u><a href="https://canvas.wisc.edu/courses/190368/files/11358475/download">virtual machine ima</a></u></strong><strong><a href="https://canvas.wisc.edu/courses/190368/files/11358475/download">g</a><u><a href="https://canvas.wisc.edu/courses/190368/files/11358475/download">e</a></u></strong> (warning: 600 MB!).

The ova file should be loaded into VirtualBox or VMware.

Once the BoxesX VM is running, you will want to start X Window System and run the Iceweasel browser, as described below.

The user name and password are ‘<strong>user</strong>‘ and ‘<strong>user</strong>‘.

How to run Iceweasel

The Web server serving the Zoobar site you will be attacking is hosted inside the VM. (If you try to connect to zoobar.org outside the VM, you will get Stanford’s site, which you should not try to interact with.) Furthermore, the Web browser you’ll use to develop and test your attacks is also hosted inside the VM. It is called Iceweasel.

Iceweasel is the Debian version of Firefox (essentially the same browser, but with a different name because of licensing issues).

To start Iceweasel in BoxesX, login as user, and do the following:

<ol>

 <li>Type the<strong> startx </strong> This will start the X Window System, and a new window will be displayed with a xterm (shell) where you can enter commands. (Click the mouse to place the window.)</li>

 <li>Type <strong>iceweasel &amp;</strong> within the newly displayed xterm. This will open the Iceweasel browser. (Again, click the mouse to place the window.)</li>

 <li>In the URL bar, you can type <strong><u><a href="http://zoobar.org/">htt</a></u></strong><strong><a href="http://zoobar.org/">p</a><u><a href="http://zoobar.org/">://zoobar.or</a></u><a href="http://zoobar.org/">g</a><u><a href="http://zoobar.org/">/</a></u></strong><strong><u><a href="http://zoobar.org/"> (htt</a></u></strong><strong><a href="http://zoobar.org/">p</a><u><a href="http://zoobar.org/">://zoobar.org/) </a></u></strong>to connect to the Zoobar site. As with any project, you will want to make and keep frequent backups of your work.</li>

</ol>

<h1>Project Overview</h1>

The fictional “Zoobar Foundation” has set up a simple Web application at zoobar.org (inside the BoxesX VM), allowing registered users to post profiles and transfer “zoobar” credits between each other. Each registered user starts with 10 “zoobar” credits.

You will craft a series of attacks on zoobar.org that exploit vulnerabilities in the website design. Each attack presents a distinct scenario with unique goals and constraints, although in some cases you may be able to reuse parts of your code.

Although many real-world attackers do not have the source code for the websites they are attacking, you are one of the lucky ones: you can find the source code under <strong><em>/var/zoobar/www</em></strong> in the BoxesX VM.

The Zoobar server is actually run locally on each of your boxes. We will run your attacks after wiping clean our own local database of registered users (except the user named “attacker”). Of course this means that any data you have added while working on the assignment will not be present during grading.

Before Start

<strong>Browser:</strong> We will grade your project within the BoxesX VM, using the Iceweasel browser,  which is installed in the Boxes.

Therefore, you should test your code in the boxes on this browser. Iceweasel is essentially the same browser as Firefox, but under different branding. Anything that works in iceweasel will likely work in (the same version of) Firefox as well. There are subtle quirks in the way HTML and JavaScript are handled by different browsers, and some attacks that work in Internet Explorer (for example) may not work in Firefox (and therefore in Iceweasel). In particular, you should use the Mozilla way of adding listeners to events (see <strong><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">htt</a></u></strong><strong><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">p</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">s://develo</a></u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">p</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">er.mozilla.or</a></u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">g</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">/en/DOM/element.addEventListener</a></u></strong> <strong><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">(</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">htt</a></u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">p</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">s://develo</a></u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">p</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">er.mozilla.or</a></u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">g</a><u><a href="https://developer.mozilla.org/en/DOM/element.addEventListener">/en/DOM/element.addEventListener) </a></u></strong>).

<strong>Email script:</strong> For Attack A, you will need a server-side script to automatically email information captured by your client-side JavaScript to your user account within the Boxes. We have provided this script for you. Please review the instructions at <strong><u><a href="http://zoomail.org/sendmail.php">htt</a></u></strong><strong><a href="http://zoomail.org/sendmail.php">p</a><u><a href="http://zoomail.org/sendmail.php">://zoomail.or</a></u><a href="http://zoomail.org/sendmail.php">g</a><u><a href="http://zoomail.org/sendmail.php">/sendmail.php</a></u></strong> <strong><a href="http://zoomail.org/sendmail.php">(</a><u><a href="http://zoomail.org/sendmail.php">htt</a></u><a href="http://zoomail.org/sendmail.php">p</a><u><a href="http://zoomail.org/sendmail.php">://zoomail.or</a></u><a href="http://zoomail.org/sendmail.php">g</a><u><a href="http://zoomail.org/sendmail.php">/sendmail.php) </a></u></strong>(open this url from within the Boxes) and use that URL in your attack scripts to send emails. Again, this server is also being run locally on your own boxes machine. To check your local email, use the mutt email client (type <strong><em>mutt</em></strong> in the shell to start the client, and follow the instructions).

Attack A: Cookie Theft

Your solution is a URL starting with <strong><u><a href="http://zoobar.org/users.php">htt</a></u></strong><strong><a href="http://zoobar.org/users.php">p</a><u><a href="http://zoobar.org/users.php">://zoobar.or</a></u><a href="http://zoobar.org/users.php">g</a><u><a href="http://zoobar.org/users.php">/users.php</a></u></strong> <strong><a href="http://zoobar.org/users.php">(</a><u><a href="http://zoobar.org/users.php">htt</a></u><a href="http://zoobar.org/users.php">p</a><u><a href="http://zoobar.org/users.php">://zoobar.or</a></u><a href="http://zoobar.org/users.php">g</a><u><a href="http://zoobar.org/users.php">/users.php) </a></u></strong>?

The grader will already be logged into zoobar.org before loading your URL.

Your goal is to steal the document cookie and email it to yourself using the email script.

When sending the email with the stolen document cookie, the group name of the email has to be set to your net ID. Except for the browser address bar (which can be different), the grader should see a page that looks exactly as it normally does when the grader visits users.php. No changes to the site appearance or extraneous text should be visible. Avoiding the red warning text is an important part of this attack. (Its ok if the page looks weird briefly before correcting itself.) Hint: Here is an example attack to use as a starting point: http://zoobar.org/users.php? user=%22%3E%3Cscript%3Ealert%28document.cookie%29;%3C/script%3E

Attack B: Cross-Site Request Forgery

Your solution is a short HTML document that the grader will open using the browser.

The grader will already be logged into zoobar.org before loading your page.

Transfer 10 zoobar credits from the grader’s account to the “attacker” account. The browser should be redirected to <strong><u><a href="https://www.bing.com/">htt</a></u></strong><strong><a href="https://www.bing.com/">p</a><u><a href="https://www.bing.com/">://www.bin</a></u><a href="https://www.bing.com/">g</a><u><a href="https://www.bing.com/">.com</a></u></strong> <strong><a href="https://www.bing.com/">(</a><u><a href="https://www.bing.com/">http://www.bin</a></u><a href="https://www.bing.com/">g</a><u><a href="https://www.bing.com/">.com/) </a></u></strong><a href="https://www.bing.com/"> </a>or <strong><u><a href="https://www.google.com/">htt</a></u></strong><strong><a href="https://www.google.com/">p</a><u><a href="https://www.google.com/">://www.</a></u><a href="https://www.google.com/">g</a><u><a href="https://www.google.com/">oo</a></u><a href="https://www.google.com/">g</a><u><a href="https://www.google.com/">le.com</a></u></strong><strong><u><a href="https://www.google.com/"> (htt</a></u></strong><strong><a href="https://www.google.com/">p</a><u><a href="https://www.google.com/">://www.</a></u><a href="https://www.google.com/">g</a><u><a href="https://www.google.com/">oo</a></u><a href="https://www.google.com/">g</a><u><a href="https://www.google.com/">le.com)</a></u></strong> as soon as the transfer is complete (so fast the user might not notice).

The location bar of the browser should not contain zoobar.org at any point.

Attack C: SQL Injection

Your solution is a short HTML document that the grader will open using the browser.

The grader will not be logged into zoobar.org before loading your page.

Your HTML document should display a form with a text field and a button. The grader will type a username into the text field and press the button.

As a result, the grader should be logged into zoobar.org as the user whose name was typed in the text field. The browser’s location bar should be redirected to <strong><u><a href="http://zoobar.org/index.php">htt</a></u></strong><strong><a href="http://zoobar.org/index.php">p</a><u><a href="http://zoobar.org/index.php">://zoobar.or</a></u><a href="http://zoobar.org/index.php">g</a><u><a href="http://zoobar.org/index.php">/index.php</a></u></strong> <strong><a href="http://zoobar.org/index.php">(</a><u><a href="http://zoobar.org/index.php">htt</a></u><a href="http://zoobar.org/index.php">p</a><u><a href="http://zoobar.org/index.php">://zoobar.or</a></u><a href="http://zoobar.org/index.php">g</a><u><a href="http://zoobar.org/index.php">/index.php) </a></u></strong>, and the page should look and behave exactly as if the grader had instead typed the username and corresponding password in the legitimate zoobar.org login form.

The name the grader types in will already be registered with some password. You do not need to handle the case in which the name was not already registered.

Hint: What part of the zoobar.org PHP code handles the user login and registration, and how does it interface with the SQLite database?

Tips

If you need to transfer files from your main machine to your virtual machine,  there is a command to use:  scp -r -P 8024 &lt;your file(s)&gt; <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="2055534552601112170e100e100e11">[email protected]</a>:&lt;target path in your vm&gt;  .

The zoobar source files are here: <strong><u><a href="https://canvas.wisc.edu/courses/190368/files/11083888/download">HW2-zoobar.zip</a></u></strong>  <strong><u><a href="https://canvas.wisc.edu/courses/190368/files/11083889/download">HW2-zoomail.zip</a></u></strong>