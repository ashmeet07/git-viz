# git-viz

git-prepration-commands

---

# This repo is for prepration for git / github

- git is a *version control* system jese ek almari jo purane kapde or nae kapde sath me rakhti hey bina koi bhedhbhao ke  
- github is a *platform* where people publish repository or space where people show case there repo online jese wo admi jo placement ke time pe achanak se nae kapdo me dikha

---

## Commands for git that help you to understand the things properly

- kisi folder ko scrach se tyar karke uski history directory ke sath jodna jiska name *.git* hey jisme pure folder ki history create hoegi har commit har change ki

**initializing repo**
```bash
git init
```

---

- kisi ke project ko tapna hey to ye command hey

**make a repo clone**
```bash
git clone <repoUrl>
```

- Or jo git ke ssh terminal pe chalana hey swag se to ye
```bash
git clone git@github.com:ashmeet07/ashmeet07.git
```

- Or agar local hi chalani hey to
```bash
git clone /path/to/repo
```

**CI/CD pipelines helpfull commands**  
agar teko ci cd ni malum to dekh:
- agar tu github me yaml ki file likhe ga github deployment ke liye to usme auto configuration hota hey tere ek push pe tera project agar github pe deployed hey to ek push pe tera project **build** hoega **test** hoega fir **deploy** apne ap hogajega jo automation ko darshata hey samjha

`CI - continuous integration`

`CD - continuous delievry / continuous deployment`

Tools: GitHub  
human intervention is needed for deployment okay

```bash
git clone --depth 1 <repoUrl>
```
- ye command latest commit hi legi puri history nahi legi

```bash
git clone --branch "name dal de repo ka" --single-branch <repoUrl>
```
- agar single branch hi copy marni hey to

Code → Commit → CI (Build & Test) → CD (Deploy to Staging/Prod)  
ye logo ka kam kam karega or fir process ko automate karega

---

## Branch Change Commmand

ab ye command tumlogo ko help karegi batane me ki tumhari directory ke related or repo me or locally kitni branch hai jo tumne banai or system ke through mili hai

```bash
git branch
```

**Remote Branch**
```bash
git branch -r
```

**Local+Remote Branch**
```bash
git branch -a
```

ab agar tumlogo ko nai branch banani ho to tum ye ninja technique use karna
```bash
git branch "branch_name"
```

- ab tumlogo ko ye command tumko tumhare ek branch se dusre branch me jane me madad karegi create-switch
```bash
git checkout -b "branch_name"
```

modern jamane me chuski ka maja log new command se create-switch
```bash
git switch -c "branchname"
```

agar nai nahi banani or bus switch karna hey to
```bash
git checkout "branch_name"
git switch "Branch_name"
```

- ab agar branch ko delete karna ho to
```bash
git branch -d "branch_name"       # delte local branch
git branch -D "branch-name"       # force delete even if not merge
git push origin --delete "branch-name"   # ye remote branch ko delte kardegi
```

**Rename Branch**
```bash
git branch -m "Branch new name"           # rename current branch
git branch -m "oldname" "newname"       # rename different branch
```

**Push Branch to remote**
```bash
git push origin "branch_name"
git push -u origin "branch_name"        # set upstream branch local to remote
```

---

## Merge Commands

ab agar kisi ne change kardiya to usko latest branch me merge karna hai to fir ye chalao
```bash
git merge "branch"   # this will merge the branch to the current one
```

```bash
git merge --no-ff branch   # this will show history while merging
git merge --abort
```

agar apko kisi ka specific commit merge karna ho fir:
```bash
git merge <commit-hash>
```

agar apko bhotsare commit ek single commit me merge karna ho fir:
```bash
git merge --squash branchname
git commit -m "Merged branchname branch as one commit"
```

agar apke do HEADS pe kam chalra hai apna or ek unka to fir merge karne ke time pe koi conflict na ae to pehale apna merge kardo fir unka kardo
```bash
git merge -s ours branch     # ours means origin
git merge -s theirs branch   # theirs means their origin
```

---

## Rebase a Branch

ye main he boss 🤘  
isme hota esa hey ki agar:

```
branch1: change1-------change2--------change3
branch2: change4-------chnage5--------change6
```

ab agar apan inko kardenge merge to ye kuch esa hoega:
```
branch1: change1------change2--------change3--------change4
```

matlab ye nai history banadega merge ki purane merge ke commits ko lekar or dikhaega ese ki logo ke changes merge hue or jo conflict aega wo ek bar me hi saihoega

---

but when do rebase:
```
branch1: change1--------change2-------change3-------change4-------change5
```

isme ye history ko pura rewrite kardega or purane commits new commits ke sath add hoke latest me show hoenge harek commit ko independently handle karna padega pura ek bar me resolve nahi hoega samjhey

---

## Commit

ye commands bhot sehshilta purn hai jise satisfaction ki prapti hoti hai 😌
```bash
git commit                # normal commit
git commit -m "message"
git commit -am "message"  # this will commit all modified, save a step if you are applying on change files
```

---

## Status Pata Karo
```bash
git status
```

---

## History of commit

agar tumko hisotry me interest ho to fir commit ki history bhi dekhlena
```bash
git log
git log --oneline         # this is short log with one line per commit
```

agar tumko purane commit pe jana hai kisi file ke to likho:
```bash
git checkout -- "filename"
```

agar kisi staged ko wapis se hatana hai to ye chalao:
```bash
git reset HEAD "filename"
```

---

## Pull Commands

```bash
git pull                   # normal pull
git pull origin main       # from specific branch
git fetch                  # similar to pull
```

agar rebase karke pull karni hey to:
```bash
git pull --rebase origin main
git fetch origin main
git rebase origin/main
```

agar sab remote se pull karni hai to:
```bash
git pull --all
```

agar kuch galat hota hey to fir chalado:
```bash
git merge --abort
git rebase --abort
```

force pull karna pade to:
```bash
git fetch --all
git reset --hard origin/main
```

---

## Push Commands

agar kisi or ne changes nahi kare ho to chalao otherwise wont work fir force hi chalegi
```bash
git push --force-with-lease origin branch-name   # safer alternative for force
```

mirror command (ye command hubahu duplicate local ka remote pe phek degi):
```bash
git push --mirror origin
```

dry run the push dekhna ki push karke hoega kya:
```bash
git push --dry-run origin main
```

push all local branches:
```bash
git push --all origin
```

---

## Stash

yes locally data store karta hey means in stack store the local data. jab koi apply kare stash se to wo stack ke top se apply hoga. har naya stash top pe add hota hai.

useful at the time of merge conflict: first stash, then pull, resolve conflicts, then re-apply stash.

```bash
git stash
git stash save "message"
git stash -u   # include untracked
git stash -a   # include ignored
```

stash list:
```bash
git stash list
```

apply stash:
```bash
git stash apply
git stash apply stash@{index}
```

pop stash (apply + remove):
```bash
git stash pop
git stash pop stash@{index}
```

drop stash:
```bash
git stash drop
git stash drop stash@{index}
```

clear stash:
```bash
git stash clear
```

stash branch:
```bash
git stash branch branch-name stash@{index}
```

show stash:
```bash
git stash show
git stash show -p
```

---

## Log Commands

```bash
git log
git log --oneline
git log --oneline --graph --all
git log --pretty=format:"%h - %an, %ar : %s"
```

filters:
```bash
git log -9
git log --author="ashmeet07"
git log --grep="nav"
git log filename.txt
```

date filters:
```bash
git log --since="2020-02-10" --until="yyyy-mm-dd"
git log --after="2 weeks ago"
```

show file names:
```bash
git log --name-only
git log --name-status
```

commit range:
```bash
git log commit1..commit2
git log branch1..branch2
```

---

## Diff Command

agar apko dekhna hai ki changes jo apne kiye unke sath jo existed hai to ap diff use kartey hai jisse apko comparision ka pata chalta hai latest repo ke sath
```bash
git diff --cached
```

compare with different commit:
```bash
git diff <commit-hash>
```

compare 2 commits:
```bash
git diff commit1 commit2
```

compare 2 branches:
```bash
git diff branch1 branch2
```

file name changes:
```bash
git diff --name-only
```

remote branch compare:
```bash
git diff origin/main
```

compare staged changes:
```bash
git diff --staged
```

compare local vs remote:
```bash
git diff HEAD origin/main
```

ignore spacing changes:
```bash
git diff -w
```

specific file diff:
```bash
git diff c1 c2 filename.txt
```

directory diff:
```bash
git diff --dirstat
```

save diff to file:
```bash
git diff > changes.patch