# git-viz
git-prepration-commands

# This repo is for prepration for git / github

- git is a *version control* system jese ek almari jo purane kapde or nae kapde sath me rakhti hey bina koi bhedhbhao ke
- github is a *platform* where people publish repository or space where people show case there repo online jese wo admi jo placement ke time pe achanak se nae kapdo me dikha

## Commands for git that help you to understand the things properly

- kisi folder ko scrach se tyar karke uski history directory ke sath jodna jiska name *.git* hey jisme pure folder ki history create hoegi har commit har change ki

---

**initializing repo**
`command`
# `git init`

---

- kisi ke project ko tapna hey to ye command hey

**make a repo clone**
`command`
# `git clone <repoUrl>`

- Or jo git ke ssh terminal pe chalana hey swag se to ye
`command`
# `git clone git@github.com:ashmeet07/ashmeet07.git`

- Or agar local hi chalani hey to
`command`
# `git clone /path/to/repo`

**CI/CD pipelines helpfull commands**
agar teko ci cd ni malum to dekh
- agar tu github me yaml ki file likhe ga github deployment ke liye to usme auto configuration hota hey tere ek push pe tera project agar github pe deployed hey to ek push pe tera project **build** hoega **test** hoega fir **deploy** apne ap hogajega jo automation ko darshata hey samjha

`CI-continuous integration`

`CD-continuous delievry/ continuous deployment`

Tools: GitHub
human intervention is needed for deployment okay

`command`
# `git clone --depth 1 <repoUrl>`

- ye command latest commit hi legi puri history nahi legi

- agar single branch hi copy marni hey to
`command`
# `git clone --branch "name dal de repo ka " --single-branch <repoUrl>`

Code → Commit → CI (Build & Test) → CD (Deploy to Staging/Prod)

ye logo ka kam kam karega or fir process ko automate karega

**Branch Change Commmand**
ab ye command tumlogo ko help karegi batane me ki tumhari directory ke related or repo me or locally kitni branch hai jo tumne banai or system ke through mili hai

`command`
# `git branch`

**Remote Branch**
ye tumko remote branch dekhne me help karegi okay
`command`
# `git branch -r`

**Local+Remote Branch**
`command`
# `git branch -a`

ab agar tumlogo ko nai branch banani ho to tum ye ninja technique use karna
`command`
# `git branch "branch_name"`

- ab tumlogo ko ye command tumko tumhare ek branch se dusre branch me jane me madad karegi create-switch
`command`
# `git checkout -b "branch_name"`

modern jamane me chuski ka maja log new command se create-switch
`command`
# `git switch -c "branchname"`

agar nai nahi banani or bus switch karna hey to
`command`
# `git checkout "branch_name"`
`command`
# `git switch "Branch_name"`

- ab agar branch ko delete karna ho to
`command`
# `git branch -d "branch_name"` //delte local branch
`command`
# `git branch -D "branch-name"` //force delete even if not merge
`command`
# `git push origin --delete "branch-name"` //ye remote branch ko delte kardegi

**Rename Branch**
`command`
# `git branch -m "Branch new name"` //rename current branch
`command`
# `git branch -m "oldname" "newname"` //rename different branch

**PushBranchto remote**
`command`
# `git push origin "branch_name"`
`command`
# `git push -u origin "branch_name"` //set upstream branch local to remote

ab agar kisi ne change kardiya to usko latest branch me merge karna hai to fir ye chalao
`command`
# `git merge "branch"` //this will merge the branch to the current one

**Updated Branch ko bulawa**
`command`
# `git fetch`
`command`
# `git switch -t origin/branch-name`

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
`command`
# `git commit` //normal commit
`command`
# `git commit -m "message"`
`command`
# `git commit -am "message"` //this will commit all modified save a step if you are applying on change files

**Status Pata Karo**
`command`
# `git status`

**History of commit**
agar tumko hisotry me interest ho to fir commit ki history bhi dekhlena
`command`
# `git log`
`command`
# `gig log --oneline` //this is short log with one line per commit

*agar tumko purane commit pe jana hai kisi file ke to liko*
`command`
# `git checkout -- "filename"`

jo commit hai wo changes locally store kardeta hey jisko ham staged boltey hai
agar kisi staged ko wapis se hatana hai to ye chalao
`command`
# `git reset HEAD "filename"`

agar tumko remote repo ke changes bulane hey to 
# `command` git pull 

- from specific branch 
# `command` git pull origin main

- ise milti julti command 
# `command` git fetch  
# `or git merge`

agar rebase karke pull karni hey to 
# `command` git pull --rebase origin main

# `command` git fetch origin main
# `command` git rebase origin/main

agar sab remote se pull karni hai to 
# `command` git pull --all


jo git fetch origin hey wo sirif fetch karegi baki rebase karna padega origin/main karke or merge 

agar kuch galat hota hey to fir chalado 
# `command` git merge --abort  
# `command` git rebase --abort


- agar force pull karna pade to fir 
# `command` git fetch --all 
# `command` git reset --hard origin/main


**Push Commands**

- Push wali commands 

agar kisi or ne changes nahi kare ho to chalao other wise wont work fir force hi chalegi
# `command` git push --force-with-lease origin branch-name //safer or alternative for  `git push --force origin main`

mirror command
ye command hubahu duplicate local ka remote pe phek degi

# `command` git push --mirror origin 


dry run the push dekhna ki push karke hoega kya 
# `command` git push --dry-run origin main


push all local branches 
# `command` git push --all origin //sare origin pe 

**Stash** ye locally data store karta hey means in stack store the local data when some one apply the stash from the top of stack the stack will be applied and newly added stash will goes on top of stack each time when user stash local changes also usefull at the time of merge conflict to resolve 


agar merge conflict ki error ajae to first stash then pull when merge conflict solve then merge the stash what you have applied on locally 

# `command` git stash

agar apko custom tag lagana ho to fir 

# `command` git stash save "message"

agar apko untracked files ko stash me lana ho to lagae
# `command` git stash -u 

or agar koi file history se ignored hai to apko lagana hoga
# `command` git stash -a

agar apko end me or pehle apki stash stack ki list dekhni hogi to simple 
# `command` git stash list

or agar final apko apne local changes apply karne hai to kare 
# `command` git stash apply 

for specific stash 
# `command` git stash apply stash@{indexofthestash}

agar apko koi apna stash remove+apply karna hai to pop kare stack se 
# `command` git stash pop

specific 
# `command` git stash pop stash@{indexofstash}

properly delte hi karna hai bina lagai to 
# `command` git stash drop

specific 
# `command` git stash drop stash@{indexofstash}

puri stack clear karni hai to 
# `command` git stash clear

agar apko apna stash kisi new branch me lagana hai to 
# `command` git stash branch branch-name stash@{indexofstash}

agar apko kisi stash ka content dekhna hai to lagae
# `command` git stash show 

agar apko full difference ke sath dekhna hai with latest to 
# `command` git stash show -p


**merge karneki command**

# `command` git merge

# `command` git merge --no-ff branch //this will show history while merging 

# `command` git merge --abort


agar apko kisi ka specific commit merge karna hoe fir 
# `command` git merge <commit-hash>

agar apko bhotsare commit ek single commit me merge karna hoe fir 
# `command` git merge --squash branchname
# `command` git commit -m  "Merged branchname brash as one commit"

agar apke do HEADS pe kam chalra hai apna or ek unka to fir merge karne ke time pe koi conflict na ae to pehale apna merge kardo fir unka kardo 

# `command` git merge -s ours branch //ours means origin 
# `command` git merge -s theirs branch //theirs means their origin
agar apko repo ki history talash ni hay to app log lagao ge
# `git log`

agar apko dekhna hai one per commit 
# `git log --oneline`

agar apko graph ke view me dekhni hai to aplagaenge 
# `git log --oneline --graph --all`

agar apko log kisi saji hui gadi jese dhekhnai hai jo apne jiwan me pehli baar li hai to 
# `git log --pretty=format:"%h -%an,%ar:%s"`

h - short hash 
an - author name
ar- relative date
s - subject 

agar apko filter karna hai to kare
# `git log -9` //jisse apkepass 9 hi log aenge

agar apko dekhna hai ki kisi specific author ke liye 
# `git log --author="ashmeet07"`

agar apko kisi specific word ke liye dekhne hai to 
# `git log --grep="nav"`

agar apko kisi specific file ke liye dekhne hoe to 
# `git log --filename.txt`

agar apko dekhna hai ki commit witin a date range 
# `git log --since="2020-02-10" --until"yyyy-mm-dd"`

agar apko kisi date ke baad dekhna hai fir 
# `git log --after="2 weeks ago"`


ye apko files ke name degi jo modified hogai 
# `git log --name-only` 

ye apko names ke sath sath status bhi degi
# `git log --name-status`


ye apko commits ki range degi 

# `git log commit1..commit2`

ye apko branch ke bich ke commit ki rnage degi compare karke 
# `git log branch1..branch2`


**Diff Command** Agar apko dekhna hai ki changes jo apne kiye unke sath jo existed hai to ap diff use kartey hai jisse apko comparision ka pata chalta hai latest repo ke sath 
# `git diff --cached`

compare with different commit agar apko kisi or commit ke sath changes compare karne hai to use kare
# `git diff <comit-hash>`

agar apko kisi do commit ka change dekhna hai to 
# `git commit1 commit2`

agar apko compare karni hai koi do branch 
# `git branch1 branch2`

agar apko koi file name dekhni hai ki change hui hai to 
# `git diff --name-only`

agar apko kisi remote branch ke sath comparision karna ho 
# `git diff origin/main`

agar apko stagged changes ke sath compare karna hai to 
# `git diff --staged`

agar tumko local commit or remote branch mai fark dekhna hai to 
# `git diff HEAD origin/main`

agar spacing badli ho to ignore changes okay 
# `git diff -w`

check for specific file across commits 
# `git diff c1 c2 filename.txt`

agar apko kisi directory ka pata karna ho ki name badla ya nahi 
# `git diff --dirstat`

agar kisi diff ko file me save karna ho to 
# `git diff > changes.patch`