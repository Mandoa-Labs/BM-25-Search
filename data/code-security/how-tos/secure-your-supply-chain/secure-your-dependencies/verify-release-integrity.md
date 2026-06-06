# Verifying the integrity of a release

You can avoid tampering and accidental changes by ensuring the releases you use have not been modified after publication.

<div class="ghd-tool cli">

## Prerequisites

Before you can validate the authenticity of a release and its assets on the command line, you need to [install the GitHub CLI](https://github.com/cli/cli?tab=readme-ov-file\&ref_product=supply-chain-security\&ref_type=engagement\&ref_style=text#installation).

## Verifying immutable releases and local artifacts

1. On the command line, open the repository containing the release you want to verify.

2. To verify a release exists and is immutable, run the following command:

   ```bash copy
   gh release verify RELEASE-TAG
   ```

3. To verify a local artifact is an exact match for a release asset, run the following command:

   ```bash copy
   gh release verify-asset RELEASE-TAG ARTIFACT-PATH
   ```

   > \[!NOTE]
   > This command cannot be used to verify the source code zip file or tarball for a release, since these assets are only created when a download is requested.

</div>

<div class="ghd-tool webui">

1. On GitHub, navigate to the main page of the repository.
2. To the right of the list of files, click **Releases**.

   ![Screenshot of the main page of a repository. A link, labeled "Releases", is highlighted with an orange outline.](/assets/images/help/releases/release-link.png)
3. To the left of the release you want to verify, below the release author, confirm that "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-lock" aria-label="lock icon" role="img"><path d="M4 4a4 4 0 0 1 8 0v2h.25c.966 0 1.75.784 1.75 1.75v5.5A1.75 1.75 0 0 1 12.25 15h-8.5A1.75 1.75 0 0 1 2 13.25v-5.5C2 6.784 2.784 6 3.75 6H4Zm8.25 3.5h-8.5a.25.25 0 0 0-.25.25v5.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-5.5a.25.25 0 0 0-.25-.25ZM10.5 6V4a2.5 2.5 0 1 0-5 0v2Z"></path></svg> Immutable" is present.

</div>