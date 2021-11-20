# İleri Git

`git log `| Shows history of commits with ID, author and date

```C:\Users\ali\Desktop\ileri_git>git log
commit 078bd570243d171b42167022bbad155a3fb0787a (HEAD -> master)
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:29:57 2021 +0300
```

    Master2 | Açıklama eklendi

```
commit 4012b2bec3e71bdc617f1d35cb7e60f6b133f2ed
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:28:22 2021 +0300    
```

`git commit --amend -m "Master 2 | Bu amend ile ekleniş yeni bir mesaj."`
`git commit --amend -m "Master 2 | Bu amend ile ekleniş yeni bir mesaj."`

Son commite yeni değişiklik eklemek yada sadece comment mesajını 
değiştirmek için amend yapılır.Aşağıda commit mesajı değilmiş log.

```
C:\Users\ali\Desktop\ileri_git>git log
commit c9540db56477896185146ba11153854a0c967c28 (HEAD -> master)
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:29:57 2021 +0300
```

    Master 2 | Bu amend ile ekleniş yeni bir mesaj.

```
commit 4012b2bec3e71bdc617f1d35cb7e60f6b133f2ed
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:28:22 2021 +0300
```

`git log -n 1`| Sondan birinci commiti getir.
`git log -n 2`| Sondan ikinci commiti getir.

`git revert idOfTheLog` | Id si verilen commite revert
eder ve loga işler. 

````
C:\Users\ali\Desktop\ileri_git>git log
commit d8f4222577630b496e1c07b0a7ba65c026d81c62 (HEAD -> master)
Author: KereBere <alsydm091@gmail.com>
Date:   Sat Nov 20 00:14:36 2021 +0300
````

    Revert "Master 3 | Liste eklendi"

    This reverts commit ea8c444eff3da08c3518cdfa332b3fb27d3d8d71.

````
commit ea8c444eff3da08c3518cdfa332b3fb27d3d8d71
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:59:08 2021 +0300
````

    Master 3 | Liste eklendi

````
commit c9540db56477896185146ba11153854a0c967c28
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:29:57 2021 +0300
````

    Master 2 | Bu amend ile ekleniş yeni bir mesaj.

````
commit 4012b2bec3e71bdc617f1d35cb7e60f6b133f2ed
Author: KereBere <alsydm091@gmail.com>
Date:   Fri Nov 19 23:28:22 2021 +0300
````

    Master 1 | Başlık eklendi

You can also revert the revert to revert changes

`git reset --hard commitID` Reverts to a commit and deletes all between

`C:\Users\ali\Desktop\ileri_git>git reset --hard 47e69a4cc6ba7a966be6e
HEAD is now at 47e69a4 MAster 3 | Liste eklendi.`
Hard reset deleted commits between & made head given commit.

`git diff firstCommitID..SecondCommitID index.html` Shows the difference between commits for index.html file. 

----------------------

`git checkout -b header` Creates and checkout to a new branch from current branch and copies what current branch has. 
`git branch -D header` Deletes the branch 
`git merge header` Merge header to current branch


`git stash` Son committen sonra yapılan çalışmaları siler/alır saklar. Log tutmaz
`Saved working directory and index state WIP on header: 59b2fdc Header  || Buttons added`
`git stash list` Son moccitten sonraki değişiklikler geçici olarak tutulur.
``stash@{0}: WIP on header: 59b2fdc Header || Buttons added``
`gis stash clear` Clears the stash list. So it is empty
`git stash pop` En üstteki stası geri getir/yükle ve stashten sil.
`git stash apply stash@{0}` Stash'ı geri getir ama ``git stash list``'ten silme 

-------------------------------------

Commit yapmadan checkout yapılamaz bir branchtan 

``git merge header `` Merges header with master/current branch that user on

Son ortak committen sonra birleştirme yapar. 
```
C:\Users\ali\Desktop\ileri_git>git merge header
Updating 7bfb1b7..39b8abf
Fast-forward
 header.md | 9 +++++++++
 index.md  | 4 +++-
 2 files changed, 12 insertions(+), 1 deletion(-)
 create mode 100644 header.md
```

`git merge --squash footer` 

```
C:\Users\ali\Desktop\ileri_git>git merge --squash footer 
Automatic merge went well; stopped before committing as requested
Squash commit -- not updating HEAD
```
Merge yapmanın aksine squash birleşmeden önce son bir commit yapmaya olanak sağlar.Aşağıda commit eklenince birleşmeye devam edildi ve tamamlandı. Merge ve squash
merge farkı, merge bütün commitleri ile gelir fakat mer squash sonda verilen
tek komutu ile gelir.

```
C:\Users\ali\Desktop\ileri_git>git commit -m "Footer Master ile birleştirildi
[master dddf5e9] Footer Master ile birleştirildi
 1 file changed, 1 insertion(+)
 create mode 100644 footer.md
```

Loga merge squash sonrası eklenen log.

```
C:\Users\ali\Desktop\ileri_git>git log
commit dddf5e9dd9b3b8a5b69268e008042081de67ba93 (HEAD -> master)
Author: KereBere <alsydm091@gmail.com>
Date:   Sat Nov 20 13:52:27 2021 +0300

    Footer Master ile birleştirildi
```

Hard reset to a given ID. Deleted all between
```
C:\Users\ali\Desktop\ileri_git>git reset --hard 47e69a4cc6ba7a966be6e
HEAD is now at 47e69a4 MAster 3 | Liste eklendi.
```

Birleştirilme yapıldı fakat loga merge edildiğine dair birşey girilmedi. 
Ama commitler girildi loga. 
```
C:\Users\ali\Desktop\ileri_git>git rebase header
Successfully rebased and updated refs/heads/master.
```

Aynı dosyalar merge edilirken ve farklı iseler conflict çıkar. Hangisinin tutulacağına kullanıcı
karar verir. 
```
C:\Users\ali\Desktop\ileri_git>git merge header
Auto-merging index.md
CONFLICT (content): Merge conflict in index.md
Automatic merge failed; fix conflicts and then commit the result.
```
Burada index.md dosyasında bir conflict var. Hangisini tutacağımız bize kalmış. 
Üstteki bizim committen gelen kod, alttaki ise merge edilen, uzaktan gelen kod.
```
<<<<<<< HEAD
- 1. MASTER Burada bir paragraf vardır...
- 2. MASTER Burada bir paragraf vardır...

=======
- 1. HEADER Burada bir paragraf vardır...
- 2. HEADER Burada bir paragraf vardır...
>>>>>>> header
## HEADER Branch üzerinden gelen değişiklik
```

`git merge --abort` Conflictli merge geri almada kullanılır. 