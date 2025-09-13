# git-viz
git-prepration-commands

# This repo is for prepration for git / github

- git is a *version control* system jese ek almari jo purane kapde or nae kapde sath me rakhti hey bina koi bhedhbhao ke
- github is a *platform* where people publish repository or space where people show case there repo online jese wo admi jo placement ke time pe achanak se nae kapdo me dikha

## Commands for git that help you to understand the things properly

- kisi folder ko scrach se tyar karke uski history directory ke sath jodna jiska name *.git* hey jisme pure folder ki history create hoegi har commit har change ki

---

**initializing repo**
`command git init`

---

- kisi ke project ko tapna hey to ye command hey

**make a repo clone**
`command git clone <repoUrl>`

- Or jo git ke ssh terminal pe chalana hey swag se to ye
`command git clone git@github.com:ashmeet07/ashmeet07.git`

- Or agar local hi chalani hey to
`command git clone /path/to/repo`

**CI/CD pipelines helpfull commands**
agar teko ci cd ni malum to dekh
- agar tu github me yaml ki file likhe ga github deployment ke liye to usme auto configuration hota hey tere ek push pe tera project agar github pe deployed hey to ek push pe tera project **build** hoega **test** hoega fir **deploy** apne ap hogajega jo automation ko darshata hey samjha

`CI-continuous integration`
`CD-continuous delievry/ continuous deployment`

Tools: GitHub
human intervention is needed for deployment okay

`command git clone --depth 1 <repoUrl>`

- ye command latest commit hi legi puri history nahi legi

- agar single branch hi copy marni hey to
`command git clone --branch "name dal de repo ka " --single-branch <repoUrl>`

Code → Commit → CI (Build & Test) → CD (Deploy to Staging/Prod)

ye logo ka kam kam karega or fir process ko automate karega

**Branch Change Commmand**
ab ye command tumlogo ko help karegi batane me ki tumhari directory ke related or repo me or locally kitni branch hai jo tumne banai or system ke through mili hai

`command git branch`

**Remote Branch**
ye tumko remote branch dekhne me help karegi okay
`command git branch -r`

**Local+Remote Branch**
`command git branch -a`

ab agar tumlogo ko nai branch banani ho to tum ye ninja technique use karna
`command git branch "branch_name"`

- ab tumlogo ko ye command tumko tumhare ek branch se dusre branch me jane me madad karegi create-switch
`command git checkout -b "branch_name"`

modern jamane me chuski ka maja log new command se create-switch
`command git switch -c "branchname"`

agar nai nahi banani or bus switch karna hey to
`command git checkout "branch_name"`
`command git switch "Branch_name"`

- ab agar branch ko delete karna ho to
`command git branch -d "branch_name"` //delte local branch
`command git branch -D "branch-name"` //force delete even if not merge
`command git push origin --delete "branch-name"` //ye remote branch ko delte kardegi

**Rename Branch**
`command git branch -m "Branch new name"` //rename current branch
`command git branch -m "oldname" "newname"` //rename different branch

**PushBranchto remote**
`command git push origin "branch_name"`
`command git push -u origin "branch_name"` //set upstream branch local to remote

ab agar kisi ne change kardiya to usko latest branch me merge karna hai to fir ye chalao
`command git merge "branch"` //this will merge the branch to the current one

**Updated Branch ko bulawa**
`command git fetch`
`command git switch -t origin/branch-name`

**Rebase a branch**
ye main he boss
isme hota esa hey ki agar
branch1: change1-------change2--------change3
branch2: change4-------chnage5--------change6
ab agar apan inko kardenge merge do ye kuch esa hoega

branch1: change1------change2--------change3--------change4

matlab ye nai history banadega merge ki purane merge ke commits ko lekar or dikhaega ese ki logo ke changes merge hue or jo conflict aega wo ek barme hi saihoega

but when do rebase

branch1: change1--------change2-------change3-------change4-------change5
isme ye history ko pura rewrite kardega or purane commits new commits ke sath add hoke latest me show hoenge harek commit ko independently handle karna padega pura ek bar me resolve nahi hoega samjhey

**Commit**
ye commands bhot sehshilta purn hai jise satisfaction ki prapti hoti hai
`command git commit` //normal commit
`command git commit -m "message"`
`command git commit -am "message"` //this will commit all modified save a step if you are applying on change files

**Status Pata Karo**
`command git status`

**History of commit**
agar tumko hisotry me interest ho to fir commit ki history bhi dekhlena
`command git log`
`command gig log --oneline` //this is short log with one line per commit

*agar tumko purane commit pe jana hai kisi file ke to liko*
`command git checkout -- "filename"`

jo commit hai wo changes locally store kardeta hey jisko ham staged boltey hai
agar kisi staged ko wapis se hatana hai to ye chalao
`command git reset HEAD "filename"`