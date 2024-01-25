An archive of a commit ID will always have the same file contents whenever it's requested, assuming the commit ID is still in the repository and the repository's name has not changed.
Because branches and tags can move to different commit IDs, future downloads of an archive may have different contents than previously downloaded archives of the same branch or tag. Assuming the branch or tag still points at the same commit ID, it will have the same file contents.
The exact compression settings used to generate a zipball or tarball may change over time. The extracted contents won't change if the branch or tag doesn't change, but the outer compressed archive may have a different byte layout. GitHub will give at least six months' notice before changing compression settings.
The name of the repository is part of the directory structure inside the archive. Therefore, if the repository name changes, the root directory name will change as well.
If you rely on stability of source code archives for reproducibility (ensuring you always get identical files inside the archive), we recommend using the archives REST API with a commit ID for :ref. Using the commit ID ensures you'll always get the same file contents inside the archive and you’ll be immune to repositories rewriting tags or moving branch heads.

If you rely on stability of archives for security (for example: to ensure you don't attempt to unzip a maliciously-crafted file), we recommend using releases instead of using source downloads. For more information, see "About releases."

You can use something like this third-party GitHub action to create and push these files as part of your release process. The Release Assets REST API can later be used to retrieve them.
