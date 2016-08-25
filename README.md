`git-resolve-conflict <strategy> <filename>`
> Resolve merge conflict in one file, using given strategy (--ours, --theirs, --union)
>
>     git-resolve-conflict --ours package.json

Installation
-----------

  - copy `/lib/git-resolve-conflict.sh` to your `.bashrc`, or
  - `npm install -g git-resolve-conflict`

 [![Get it on npm](https://nodei.co/npm/git-resolve-conflict.png?compact=true)](https://www.npmjs.org/package/git-resolve-conflict)

TL;DR
=====

It's just a tiny wrapper around [git-merge-file](https://git-scm.com/docs/git-merge-file) to simplify the API. See `./lib/git-resolve-conflict.sh`.

I used temp files instead of process substitution to make it msys/mingw-friendly.


Description
===========

only if `foobar.json` is *the only file that was modified*; on any other files modified, the merge should fail)
**Check `./lib/git-resolve-conflict.sh` in this repo!**
`git-resolve-conflict` to the rescue
    me@mymachine /d/gh/merge-file-ours-poc (merge_master_to_develop +|MERGING)
    $ git diff --cached
    diff --git a/added-in-master.txt b/added-in-master.txt
    new file mode 100644
    index 0000000..9cef8af
    --- /dev/null
    +++ b/added-in-master.txt
    @@ -0,0 +1 @@
    +added in master
    diff --git a/package.json b/package.json
    index 75c469b..03f513b 100644
    --- a/package.json
    +++ b/package.json
    @@ -6,6 +6,10 @@
       "scripts": {
         "test": "echo \"Error: no test specified\" && exit 1"
       },
    +  "dependencies": {
    +    "foobar": "1.0.0",
    +    "quux": "2.0.0"
    +  },
       "author": "",
       "license": "ISC"
     }

            modified:   package.json