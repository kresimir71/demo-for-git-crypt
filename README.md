# demo-for-git-crypt
This repository shows the working of git-crypt
## What is it about?
There is a usefull package *git-crypt* for encrypting a git repository. As an example, a directory *src* of this repository has been encrypted.
### Other possibilities
Another tool with similar aim is
https://github.com/spwhitton/git-remote-gcrypt

## How does it work?
You install the package *git-crypt* as follows:
```
function buildgitcrypt1 () {
echo 'RUN THIS AS ROOT'
if cd /tmp
then
 rm -rf git-crypt
 git clone https://www.agwa.name/git/git-crypt.git
 cd git-crypt
 make  # youcould need  'make CXXFLAGS="-U__STRICT_ANSI__ -std=c++11"'  with some versions of cygwin
 if ! make install
 then
   echo 'E R R O R:RUN THIS AS ROOT'
 fi
else
 echo 'ERROR:there is no /tmp'
fi
}

buildgitcrypt1

```
Checkout a local copy and see that src/file1.txt is encrypted.
```
$ cd /tmp
$ git clone https://github.com/kresimir71/demo-for-git-crypt.git
Cloning into 'demo-for-git-crypt'...
remote: Enumerating objects: 24, done.        
remote: Counting objects: 100% (24/24), done.        
remote: Compressing objects: 100% (19/19), done.        
remote: Total 24 (delta 6), reused 17 (delta 4), pack-reused 0        
Unpacking objects: 100% (24/24), done.
$ cd demo-for-git-crypt/
cat src/file1.txt
GITCRYPT▒▒▒▒k▒▒f▒w,▒▒N▒.▒x▒▒#▒|▒▒▒i▒+.▒l▒▒@▒*▒(#▒8A▒▒vehQwC▒▒a\▒F9ye▒▒▒:▒▒▒a▒Mc▒▒b▒(▒▒▒?jIC▒▒▒▒
```
The key is here in this demo base64 encoded. You see the secret key below.
```
$ echo 'AEdJVENSWVBUS0VZAAAAAgAAAAAAAAABAAAABAAAAAAAAAADAAAAIEsTXN0sC27YC3RU9BiVZiSD
H20KvfYyim+O/T5j4kl5AAAABQAAAEDWHoH2ZB7GdQ+FhCluDD+z0CiaSqYMqBEj2Cn+A1T+YgH2
OnaVNeabLXOgCMsZ6DzYtYpjPx1+fq1W/hKShrJ+AAAAAA==' | base64 --decode > /tmp/my-git-crypt-key
$ git-crypt unlock /tmp/my-git-crypt-key 
$ cat src/file1.txt
git-crypt enables transparent encryption and decryption of files in a git repository.
```
