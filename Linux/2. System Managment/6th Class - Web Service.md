# Web Service
We use `apache`
```bash
fsiccatto@htb[/htb]$ sudo apt install apache2 -y
```

We start like:
```bash
fsiccatto@htb[/htb]$ sudo systemctl start apache2
```
By default, Apache will serve on HTTP port 80
To set an alternate port for our web server, we can edit the `/etc/apache2/ports.conf` file.

## Curl
`cURL` is a tool that allows us to transfer files from the shell over protocols like `HTTP`, `HTTPS`, `FTP`, `SFTP`, `FTPS`, or `SCP`, and in general, gives us the possibility to control and test websites remotely via command line. Besides the remote servers' content, we can also view individual requests to look at the client's and server's communication. Usually, `cURL` is already installed on most Linux systems. This is another critical reason to familiarize ourselves with this tool, as it can make some processes much easier later on.
```bash
fsiccatto@htb[/htb]$ curl http://localhost
```
In the title tag, we can see that it is the same text as from our browser. This allows us to inspect the source code of the website and get information from it. More specifically, `curl` returns the website’s page source as STDOUT. As opposed to viewing a website with a browser, which renders the HTML, CSS, and Javascript to create visual, aesthetic websites. Nevertheless, we will come back to this in another module.

## Wget
An alternative to curl is the tool `wget`. With this tool, we can download files from FTP or HTTP servers directly from the terminal, and it serves as a solid download manager. If we use wget in the same way, the difference to curl is that the website content is downloaded and stored locally, as shown in the following example.
```bash
fsiccatto@htb[/htb]$ wget http://localhost

--2020-05-15 17:43:52--  http://localhost/
Resolving localhost (localhost)... 127.0.0.1
Connecting to localhost (localhost)|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10918 (11K) [text/html]
Saving to: 'index.html'

index.html                 100%[=======================================>]  10,66K  --.-KB/s    in 0s      

2020-05-15 17:43:52 (33,0 MB/s) - ‘index.html’ saved [10918/10918]
```

## Python 3
In this case, the web server's root directory is where the command is executed to start the server. For this example, we are in a directory where WordPress is installed and contains a "readme.html." Now, let us start the Python 3 web server and see if we can access it using the browser.
```bash
fsiccatto@htb[/htb]$ python3 -m http.server

Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```

In penetration testing, we often find ourselves facing challenges that require creative problem solving and out-of-the-box thinking. You'll encounter scenarios you haven't dealt with before, which means not only learning something new but also figuring out solutions on your own through research and innovative thinking.