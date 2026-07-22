# Configuring a remote repository for a fork

Set up a remote pointing to the upstream repository in Git to sync changes between your fork and the original repository.

1. Open your terminal or Git Bash.
1. List the remotes currently configured for your fork.

   ```shell
   $ git remote -v
   > origin  https://github.com/YOUR-USERNAME/YOUR-FORK.git (fetch)
   > origin  https://github.com/YOUR-USERNAME/YOUR-FORK.git (push)
   ```

1. Add a new remote named _upstream_ that points to the original repository.

   ```shell
   git remote add upstream https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git
   ```

1. Verify the new upstream repository that you specified for your fork.

   ```shell
   $ git remote -v
   > origin    https://github.com/YOUR-USERNAME/YOUR-FORK.git (fetch)
   > origin    https://github.com/YOUR-USERNAME/YOUR-FORK.git (push)
   > upstream  https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git (fetch)
   > upstream  https://github.com/ORIGINAL-OWNER/ORIGINAL-REPOSITORY.git (push)
   ```