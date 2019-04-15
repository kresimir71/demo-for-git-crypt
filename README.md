# demo-for-git-crypt
This repository shows the working of git-crypt
## What is it about?
There is a usefull package *git-crypt* for encrypting a git repository. As an example, a directory *src* of this repository has been encrypted.
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
