---
id: 1028
title: How to update your hosts file.
date: 2017-08-24T09:20:36+00:00
author: Keith Greer
layout: post
guid: http://keithgreer.uk/?p=1028
permalink: /update-hosts-file
colour:
  - 'null'
menu:
  - 'null'
intro:
  - ""
alternative_title_area:
  - ""
blog_tag:
  - ""
blog_category:
  - ""
categories:
  - Notes
tags:
  - Command Line
  - Linux
  - Quickfix
---
Every computer has a file on it which allows the owner to specify where a website is loaded from. A hosts file is a simple combination of domain names and IP addresses.

Adding a record to your hosts file means your computer will load the domain using the IP address specified, rather than the one provided by DNS.

<pre>111.222.333.444 www.domain.com
111.222.333.444 domain.com
111.222.333.555 subdomain.domain.com
</pre>

<ul id="example-tabs" class="tabs" data-tabs="">
  <li class="tabs-title is-active">
    <a href="#panel1">Windows</a>
  </li>
  <li class="tabs-title">
    <a href="#panel2" data-tabs-target="#panel2">Linux</a>
  </li>
  <li class="tabs-title">
    <a href="#panel3" data-tabs-target="#panel3">MacOS</a>
  </li>
</ul>

<div class="tabs-content" data-tabs-content="example-tabs">
  <div id="panel1" class="tabs-panel is-active">
    <ol>
      <li>
        Press the Windows key.
      </li>
      <li>
        Type <strong>Notepad</strong> in the search field.
      </li>
      <li>
        Right-click on the <strong>Notepad</strong> result
      </li>
      <li>
        Select <strong>Run as administrator</strong>.
      </li>
      <li>
        From Notepad, open: <strong>C:\Windows\System32\Drivers\etc\hosts</strong>
      </li>
      <li>
        Add the new lines to the file.
      </li>
      <li>
        Click <strong>File > Save</strong> to save your changes.
      </li>
      <li>
        Exit Notepad
      </li>
    </ol>
  </div>
  
  <div id="panel2" class="tabs-panel">
    <ol>
      <li>
        Open a terminal window.
      </li>
      <li>
        Open the hosts file in a text editor (you can use any text editor) by typing the following line:<br /> <code>sudo nano /etc/hosts</code>
      </li>
      <li>
        Enter your domain user password.
      </li>
      <li>
        Make the necessary changes to the file.
      </li>
      <li>
        Save the file
      </li>
    </ol>
  </div>
  
  <div id="panel3" class="tabs-panel">
    Good luck. </p> 
    
    <p>
      <strong>Mac OS X 10.0 through 10.1.5</strong>
    </p>
    
    <ol>
      <li>
        Open <strong>/Applications/Utilities/NetInfo Manager</strong>.
      </li>
      <li>
        To allow editing of the NetInfo database, click the padlock in the lower-left corner of the window.
      </li>
      <li>
        Enter your domain user password and click <strong>OK</strong>.
      </li>
      <li>
        In the second column of the browser view, select the node named machines. <p>
          The third column contains entries for <code>-DHCP-</code>, <code>broadcasthost</code>, and <code>localhost</code>.</li> 
          
          <li>
            In the third column, select <code>localhost</code>.
          </li>
          <li>
            From the <strong>Edit</strong> menu, select <strong>Duplicate</strong>. (The quickest way to create a new entry is to duplicate an existing one.) <p>
              A confirmation alert appears.</li> 
              
              <li>
                Click <strong>Duplicate</strong>. <p>
                  A new entry called localhost copy appears, and its properties are shown below the browser view.</li> 
                  
                  <li>
                    Double-click the value of the <code>ip_address</code> property and enter the IP address of the other computer.
                  </li>
                  <li>
                    Double-click the value of the <code>name</code> property and enter the hostname you want for the other computer.
                  </li>
                  <li>
                    Click the <code>serves</code> property and select <strong>Delete</strong> from the <strong>Edit</strong> menu.
                  </li>
                  <li>
                    From the <strong>File</strong> menu, select <strong>Save</strong>. <p>
                      A confirmation alert appears.</li> 
                      
                      <li>
                        Click <strong>Update this copy</strong>.
                      </li>
                      <li>
                        Repeat steps 6 through 12 for each additional host entry that you want to add.
                      </li>
                      <li>
                        From the NetInfo Manager menu, select <strong>Quit</strong>. <p>
                          You do not need to restart the computer.</li> </ol> 
                          
                          <p>
                            <strong>Mac OS X 10.6 through 10.12</strong>
                          </p>
                          
                          <ol>
                            <li>
                              Open <strong>Applications > Utilities > Terminal</strong>.
                            </li>
                            <li>
                              Open the <strong>hosts</strong> file by typing the following line in the terminal window: <pre><code>sudo nano /private/etc/hosts
</code></pre>
                            </li>
                            
                            <li>
                              Type your domain user password when prompted.
                            </li>
                            <li>
                              Edit the <strong>hosts</strong> file. <p>
                                The file contains some comments (lines starting with the # symbol), and some default hostname mappings (for example, 127.0.0.1 – local host). Add your new mappings after the default mappings.</li> 
                                
                                <li>
                                  Save the hosts file by pressing <strong>Control+x</strong> and answering <strong>y</strong>.
                                </li>
                                <li>
                                  Make your changes take effect by flushing the DNS cache with the following command:<br /> <code>dscacheutil -flushcache&lt;br />
</code>
                                </li></ol> 
                                
                                <p>
                                  The new mappings should now take effect.
                                </p></div> </div>