#PS1 #git #bashrc 

현재 git환경인지, 어느 브랜치에 있는지 Terminal Prompt에서 보기 위하여 아래 내용 추가 
`.bashrc ` 파일에 아래 내용 추가
```bash
c_cyan=`tput setaf 6`
c_red=`tput setaf 1`
c_green=`tput setaf 2`
c_sgr0=`tput sgr0`

# Black:0, Red:1, Green:2, Yellow:3, Blue:4, Magenta:5

parse_git_branch ()
{
   if git rev-parse --git-dir >/dev/null 2>&1
   then
      gitver=$(git branch 2>/dev/null| sed -n '/^\*/s/^\* //p')
   else
      return 0
   fi
   echo -e $gitver
}

branch_color ()
{
   if git rev-parse --git-dir >/dev/null 2>&1
   then
      color=""
      if git diff --quiet 2>/dev/null >&2
      then
         color="${c_green}"
      else
         color="${c_red}"
      fi
   else
      return 0
   fi  
   echo -ne $color
}
export PS1='\[\e[0;33m\]\u\[\e[0m\]@\[\e[0;32m\]\h\[\e[0m\]:\[\e[0;34m\]\W\[\e[0m\] (\[$(branch_color)\]$(parse_git_branch)\[${c_sgr0}\])\$ '
```