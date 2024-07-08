
The source code are :


git config --global alias.tmpb '!D:/MyDoc/Git/TempBranch.bat'


TempBranch.bat :


@echo off
for /f "skip=1" %%x in ('wmic os get localdatetime') do if not defined MyDate set MyDate=%%x
for /f %%x in ('wmic path win32_localtime get /format:list ^| findstr "="') do set %%x
set fmonth=00%Month%
set fday=00%Day%
set today=%Year%-%fmonth:~-2%-%fday:~-2%
echo %today%

git checkout -B daily/%today%






git config --global alias.tmpbm '!D:/MyDoc/Git/TempBranchMergeBackToMain.bat'




TempBranchMergeBackToMain.bat



@echo off
for /f "skip=1" %%x in ('wmic os get localdatetime') do if not defined MyDate set MyDate=%%x
for /f %%x in ('wmic path win32_localtime get /format:list ^| findstr "="') do set %%x
set fmonth=00%Month%
set fday=00%Day%
set today=%Year%-%fmonth:~-2%-%fday:~-2%
echo %today%

git checkout master
git merge -m "Daily%today%"   daily/%today% --squash
git commit  -m "Daily%today%" 




git config --global alias.squash '!D:/MyDoc/Git/SquashBranch.bat'



SquashBranch.bat


git branch -D %1temp 
git branch %1temp %3~   & :: Create a temp branch starting with end of commit 
git checkout %1temp
git reset --mixed %2  & :: Soft reset to clear all commit down to start commit
git add -A  & :: Add all untracked files
git commit -a -m "squash intermeidate commits"
git cherry-pick %3~..%1  -m 1   & :: Copy commits after end commit
git branch %1 -m %1.old  & :: save source branch
git branch -m %1  & :: rename temp branch to org name









