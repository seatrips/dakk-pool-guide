# dakk-pool

This software is created by lisk delegate "dakk", 
Please consider a small donation if you use this software: "2324852447570841050L" for lisk or "7725849364280821971S" for shift. @Seatrips also likes beer :) "2640685646054674464L" for the changes.

### Prerequisitions

```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade -y
```

!!! install nodejs 6 or higher, it won't work without

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs 
sudo apt-get install -y npm
```

```
sudo apt-get install python3
sudo apt-get install python3-requests
sudo apt-get install curl
```

Clone repo

```
git clone https://github.com/dakk/lisk-pool
```

then rename folder to your own pool site if you like
Configuration

Edit config.json

    PUBKEY: your delegate pubkey

    PERCENTAGE: percentage to distribute

    SECRET: your secret

    SECONDSECRET: your second

    NODE: the lisk node where you get forging info

    NODEPAY: the lisk node used for payments

    MINPAYOUT: the minimum amount for a payout

Now edit /docs/index.html and customize the webpage. When using a dedicated server instead of github page you could put the content of docs in /var/www/html
and edit /docs/app.js

Finally edit poollogs.json and put in lastpayout the unixtimestamp (http://www.unixtimestamp.com/) of your last payout or the date of pool starting and donations adress and amount. 

Then copy to /docs folder or /html folder if using your own dedicated server instead of github page
You can also change root for apache2 to /home/user/lisk-pool/docs

### If you are using lisk or rise you need to dpos-api-fallback:

```
git clone https://github.com/vekexasia/dpos-api-fallback (this should be done in the lisk-pool folder)
cd dpos-api-fallback
npm install
npm run package
```

### Running it

```
python3 liskpool.py
```

It produces a file "payments.sh" with all payments shell commands. Run this file with:

```
bash payments.sh
```

The payments will be broadcasted (every 10 seconds). At the end you can move your generated poollogs.json to docs/poollogs.json and send the update to your git repo.

To display the pool frontend, enable docs-site on github repository settings.
Batch mode

The script is also runnable by cron using the -y argument:

```
python3 liskpool.py -y`
```

or

```
bash batch.sh 
```

This 'batch.sh' file will run liskpool, then payments.sh and copy the poollogs.json in the docs folder.

When changing path of the index.html and other files in the docs directory:

```
nano batch.sh
```
and check if its all oke

For easy documentation for running this on your own server
check https://github.com/seatrips/easy-apache2-site

## License

Copyright 2017 Davide Gessa

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
