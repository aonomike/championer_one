# How to Review a Develop Pull Request(PR)
### tl;dr commands: (unless it's a forked repo, see commands [here](#for-forked-repos))
```
git fetch origin
git checkout 45-add-waffle-badges
git pull
cd assets && npm audit
npm ci && npm audit
cd .. && mix deps.get
mix ecto.migrate && mix credo
chromedriver & mix test && pkill chromedriver
open http://0.0.0.0:4000 && mix phx.server
```

Then skip to the [Reviewing from GitHub](#reviewing-from-github) section

## Championer One procedures for merging Pull Requests dictates one review by a fellow collaborator.
  * **This way,** before the merge takes place, we have some quality control, and allow the collaborator making the request to improve their code.  

  * **So you're ready to contribute by reviewing a pull request?** *Great!* We'll walk you through the process step by step.

  * We're going to assume the PR is for `45-add-waffle-badges`.

  * **First,** go to your terminal and fetch any new branches with `git fetch origin`.

  * **Then,** navigate to the branch which you want to provide a PR review with `git checkout 45-add-waffle-badges`.

  * **Once on the PR branch,** fetch and merge with `git pull`.

  * **Next,** run `cd assets && npm audit` to see if there are any current security vulnerabilities in your modules.
  
  * **Then,** run `npm ci && npm audit` to update the node_modules and make sure no vulnerabilities remain.

  * **Having confirmed the absence of vulnerabilities,** run `cd .. && mix deps.get` to navigate back to the root of the project and install the dependencies.

  * **Then,** you'll want to migrate the database and run _Credo_, a static code analysis tool for the Elixir language with a focus on teaching and code consistency. `mix ecto.migrate && mix credo`.

  * **Now,** you are ready to run the tests to verify everything is passing. For this, you'll need to run `chromedriver & mix test && pkill chromedriver`.

  * **Having verified all the tests pass,** you can start the server with `mix phx.server` and navigate to `http:0.0.0.0:4000` in your browser to check that everything compiles correctly.

## Reviewing from GitHub
  * **The next step** is to navigate to  [Championer One's repo](https://github.com/championer-org/championer_one).

  * **Click on the Pull Request tab** to see all available PR's.

  * **Find** the Pull Request you want to review and click on it.

  * **Once** on the PR, in this case, `45-add-waffle-badges`, at the bottom of the page you will see `Review required`.

  * **Before adding your review,** check to make sure the branch is not out of date with the base branch, and if it is, `Update branch`.  

  ![championer-one-upddate-branch](https://dl.dropbox.com/s/b2tliy2md6vwlns/championer-one-update-branch.png?dl=0)

  * **If** the branch is up-to-date, it will look like this:

  ![Screenshot 2018-06-09 15.14.56.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a25cbb27cf1172d43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041183fe5837a89c43ca59f64be8485cb65e.png)

  with `Merge pull request` blocked because it needs to be reviewed.

  * **Clicking on** `Add your review` will take you to the page where you can see the changes and `Comment`, `Approve`, or `Request changes`, as appropriate.

  ![Screenshot 2018-06-09 15.28.47.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a25cbb170f1162c43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041183fe5837a89c43ca59f64be84c57b65e.png)

  * **Assuming you approve** the Pull Request, you will be taken back to the PR and prompted to `Merge pull request` with everything in green.

  ![Screenshot 2018-06-09 15.31.46.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a25cbb079f1162d43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041083fe5837a89c43ca59f64ae14450b65e.png)

  * **Then,** `Confirm merge` to finish your PR review.

  ![Screenshot 2018-06-09 15.32.15.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a25cbb07af1132e43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041183fe5837a89c43ca59f64be84a51b65e.png)
## Troubleshooting  
  * **Sometimes,** there will be conflicts that must be resolved before making your review.

  ![Screenshot 2018-06-09 16.37.40.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb07ff1162b43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041083fe5837a89c43ca59f64be84c54b65e.png)

  * **Working through conflicts,** via the command line, is straightforward using these instructions, provided by GitHub.

  ![Screenshot 2018-06-09 16.40.40.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb778f1162b43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041183fe5837a89c43ca59f64be84456b65e.png)

  * **If you prefer,** you can also click on the `Resolve conflicts` link which will take you to the merge conflicts.
  * **For each file with a merge conflict,** you'll click on `Mark as resolved` so you can move on to the next one:
  ![Screenshot 2018-06-09 16.42.47.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb77af1162c43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041183fe5837a89c43ca59f64be84b50b65e.png)

  ![Screenshot 2018-06-09 16.43.17.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb77bf1132c43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041183fe5837a89c43ca59f64be84450b65e.png)

  * **View the following file,** and click `Next` to cycle through the conflicts in the file, if there are more than one:
  ![Screenshot 2018-06-09 16.44.15.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb77cf1132e43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041083fe5837a89c43ca59f64be8445db65e.png)

  * **Be sure to remove the branch name comments** and the equals sign line, as you decide how to resolve:
  ![Screenshot 2018-06-09 16.55.52.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb67df1172943434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041083fe5837a89c43ca59f64ae14452b65e.png)
  
  * **Click on** `Commit merge` to kickoff the full update of the branch:
  ![Screenshot 2018-06-09 16.59.00.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a26cbb671f1122b43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041e83fe5837a89c43ca59f64be84952b65e.png)

* **As the develop branch merges,** you will be taken back to the Pull Request where you can make your review.

  ![Screenshot 2018-06-09 17.04.36.png](https://waffleio-direct-uploads-production.s3.amazonaws.com/uploads/57e387b76082a50f00d31003/125516c66e82c728ace21e0d46db978826878dba87e6ab03f60da1cc6416713e795de37a27cbb37cf1112d43434d0eee1e020a17b8eb8339a3e43c71895f58ead0695926cf6911acb08b17b606ba20de5d99a4fedb1294b7607caddecd5d340c041083fe5837a89c43ca59f64ae1445db65e.png)

* **Thank you for your collaboration in reviewing Pull requests. This is an essential part of working as a team to improve code.**
 

## For forked repos
### tl;dr commands (actually, if you read the [step-by-step instructions for a non-forked repo](#championer-one-procedures-for-merging-pull-requests-dictates-one-review-by-a-fellow-collaborator), then these are very similar.

![example forked repo](https://camo.githubusercontent.com/5c6f58d6502efecfa1d35119cd362f311227d2eb/68747470733a2f2f646c2e64726f70626f782e636f6d2f732f717570786161783171776c6a3038642f53637265656e73686f74253230323031382d31302d313225323030302e31352e31332e706e67)

With this example, you can run the following commands:
```
git remote add pedro https://github.com/PedroPovedaQ/championer_one
git fetch pedro
git checkout 97-deprecation-fix
git pull
cd assets && npm audit
npm ci && npm audit
cd .. && mix deps.get
mix ecto.migrate && mix credo
chromedriver & mix test && pkill chromedriver
open http://0.0.0.0:4000 && mix phx.server
```
Then jump back to the [Reviewing from GitHub](#reviewing-from-github) section
