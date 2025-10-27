# Esercizio di risoluzione di un merge conflict

**Il tempo massimo in laboratorio per questo esercizio è di _20 minuti_.
Se superato, sospendere l'esercizio e riprenderlo per ultimo!**

Si visiti https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.
Questo repository contiene due branch: `master` e `feature`

Per ognuna delle seguenti istruzioni, si annoti l'output ottenuto.
Prima di eseguire ogni operazione sul worktree o sul repository,
si verifichi lo stato del repository con `git status`.

1. Si cloni localmente il repository
git clone https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.git
Cloning into 'OOP-git-merge-conflict-test'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 12 (delta 1), reused 1 (delta 1), pack-reused 8 (from 1)
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (2/2), done.
PS C:\Users\tobias.basilisco\Documents\OOP\LAB\lab06-repos> 

2. Ci si assicuri di avere localmente entrambi i branch remoti
>git log --all --graph
* commit bed943fbdd6ba94e64197448e4754a529d984e88 (origin/feature)
| Author: Danilo Pianini <danilo.pianini@gmail.com>
| Date:   Thu Oct 27 17:21:22 2016 +0200
|
|     Print author information
|
| * commit 8e0f29c12e060f3bdc62540343eff3e473616d61 (HEAD -> master, origin/master, origin/HEAD)
|/  Author: Danilo Pianini <danilo.pianini@gmail.com>
|   Date:   Thu Oct 27 17:19:05 2016 +0200
|
|       Change HelloWorld to print the number of available processors
|
* commit d956df66aeb0829f23b7b3d0d9a1c002c390f87f
| Author: Danilo Pianini <danilo.pianini@gmail.com>
| Date:   Thu Oct 27 17:17:43 2016 +0200
|
|     Create .gitignore
|
* commit 700ee0b669f6cd75384abb9af51ca5c2adefe917
  Author: Danilo Pianini <danilo.pianini@gmail.com>
  Date:   Thu Oct 27 17:15:10 2016 +0200

3. Si faccia il merge di `feature` dentro `master`, ossia: si posizioni la `HEAD` su `master`
   e da qui si esegua il merge di `feature`
git checkout master  
Already on 'master'
Your branch is up to date with 'origin/master'.
git merge origin/feature
Auto-merging HelloWorld.java
CONFLICT (content): Merge conflict in HelloWorld.java
Automatic merge failed; fix conflicts and then commit the result.
4. Si noti che viene generato un **merge conflict**!
5. Si risolva il merge conflict come segue:
   - Il programma Java risultante deve stampare sia il numero di processori disponibili
     (funzionalità presente su `master`)
     che il nome dell'autore del file
     (funzionalità presente su `feature`)
6. Si crei un nuovo repository nel proprio github personale
7. Si aggiunga il nuovo repository creato come **remote** e si elenchino i remote
git remote add personal-repo https://github.com/Tobias-Basilisco/OOP-git-merge-conflict-test.git
PS C:\Users\tobias.basilisco\Documents\OOP\LAB\61\OOP-git-merge-conflict-test> git remote -v
origin  https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.git (fetch)
origin  https://github.com/APICe-at-DISI/OOP-git-merge-conflict-test.git (push)
personal-repo   https://github.com/Tobias-Basilisco/OOP-git-merge-conflict-test.git (fetch)
personal-repo   https://github.com/Tobias-Basilisco/OOP-git-merge-conflict-test.git (push)
8. Si faccia push del branch `master` sul proprio repository
git push personal-repo
info: please complete authentication in your browser...
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 24 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 439 bytes | 439.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Tobias-Basilisco/OOP-git-merge-conflict-test.git
   8e0f29c..51b072f  master -> master
9. Si setti il branch remoto `master` del nuovo repository come *upstream* per il proprio branch `master` locale
it branch --set-upstream-to=personal-repo/master
branch 'master' set up to track 'personal-repo/master'.