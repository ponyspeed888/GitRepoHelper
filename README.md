[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FGitRepoHelper&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

The repo contain a few simple custom git commands that are very useful, yet missing in git standard command

LocalOnlyGitRepoHelper : Commands assume that you have only a single local repo, no remote repo
* git tmpb (from any branch): create and switch a daily branch in folder daily/\<yyyy-mm-dd>, always create from HEAD of master
* git tmpbm (from any branch) : squash merge the daily branch into master.  No need to specify either branches, because they are hard coded as today's daily branch and master
* git squash \<branchName> \<BottomCommit> \<TopCommit> (from the branch you want to squash) :  
      It will be rename branch to  \<branchName>.old, so if anything go wrong, you can go back. Remove any commit between \<BottomCommit> and \<TopCommit>, exclusively.  Replace the deleted commit with a auto generated message. This is like git rebase -i, except it does not require any interaction.  Used to remove commit history if you have a lot of them. This command only work if there is no conflict to solve.




