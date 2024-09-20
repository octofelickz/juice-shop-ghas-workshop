# Lab 5 - Hands-on with Secret Scanning

Let's use Secret Scanning with push protections to prevent secrets from entering the codebase!

## Exercise 1: Attempt to commit a secret

1. Let's try to commit a secret to the repository to test out the secret scanning push protection feature.
2. But first, we need a secret to commit! The easiest is to generate a GitHub personal access token (with limited scopes) and attempt to commit it.
3. In a new browser tab, navigate to github.com and click on your **user profile picture** in the upper right and click on **Settings**.
4. Expand **Developer settings** on the lower left.
5. Click on **Personal Access Tokens (classic)**.
6. Generate a **new token** (**classic**).
7. We don't have to give the token any scopes here - just give it a **name** and scroll down to the bottom and **Generate**.
8. Copy the token.
9. Now, let's attempt to commit the token to the repository. You can do this in Codespaces or in the web browser.
10. Any file would work, but for example, we can open up the `routes/login.ts` file we edited earlier.
11. As an example, on line 19 you can add `const secret = "<YOUR TOKEN>";`, replacing `<YOUR TOKEN>` with the token you just generated - it should start with `ghp_`.
12. Save and commit the file. If in the UI, the push will happen as you commit. If in Codespaces, you will have to push separately to a non-main branch.
13. Push protection should detect the GitHub personal access token and block the push - great!
    1. If using the browser, you will see a message with a red banner that the push was blocked.
    2. If using Codespaces review the git output in the terminal. It should provide information on why the push was blocked (because of the secret scanning push protection).
    3. As an GitHub organization owner, you can add in a link that appears in the terminal output that links to a GitHub wiki, readme, etc. that explains to the developer on how to resolve the issue. For example, you can instruct the developer to run a `git reset HEAD~1`, where `1` is the number of commits they need to rewind in order to remove the commit with the secret.
14. Depending on how the settings are configured, we could bypass the push protection and push the secret to the repository. But, we don't want to do that! 🙅‍♂️ Repository admins and organization owners would receive an email notification if we did.
15. BONUS: If you used the browser to commit a secret, switch to Codespaces and try to commit and push the secret. If you used Codespaces, try using the browser to commit and push the secret. See how the experience differs, but the end result is still the same: no secrets committed to the repository!

## Exercise 2: Managing Secret Alerts

TODO: Do we want an exercise here on closing a secret alert manually? We can pretend that for one of the secret alerts, we went to the cloud provider and revoked the token, so now we can go and close the alert and note that on the repo. See comment: https://github.com/joshjohanning-org/universe2024-ghas-workshop/pull/1/files/71e88234cd01574b5c4747cc313b3e10b2f6f678#r1760213523

## Summary

Celebrate 🎉! We just prevented a secret from entering our codebase!

And there you have it. You should now have a good grasp on what GitHub Advanced Security is, how it works, and how to implement it. So get out there and keep your company secured!