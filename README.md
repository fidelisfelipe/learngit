# learngit
Estudo de conceitos e técnicas

#1.1 projeto criado primeiro que o repositórioo
cmd> git init
cmd> git add .
cmd> git commit -m"primeiro commit - hello git"output>
[master (root-commit) f6b87bb] primeiro commit - hello git
warning: LF will be replaced by CRLF in .gitignore.
The file will have its original line endings in your working directory.
 12 files changed, 118 insertions(+)
 create mode 100644 .classpath
 create mode 100644 .gitignore
 create mode 100644 .project
 create mode 100644 .settings/.jsdtscope
 create mode 100644 .settings/org.eclipse.jdt.core.prefs
 create mode 100644 .settings/org.eclipse.wst.common.component
 create mode 100644 .settings/org.eclipse.wst.common.project.facet.core.xml
 create mode 100644 .settings/org.eclipse.wst.jsdt.ui.superType.container
 create mode 100644 .settings/org.eclipse.wst.jsdt.ui.superType.name
 create mode 100644 WebContent/META-INF/MANIFEST.MF
 create mode 100644 WebContent/WEB-INF/web.xml
 create mode 100644 WebContent/index.html

#conferi o meu commit

cmd>git log
output>
* commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07
  Author: Fidelis Guimaraes <Fidelis Guimaraes>
  Date:   Wed Feb 3 09:38:52 2016 -0200

      primeiro commit - hello git
#depois foi criado o repositório remoto no git com um arquivo Readme.mdd
* commit dd81114e97fe735fe5d90901c4e46bebb6818072
  Author: Fidelis Felipe <atosfiel@gmail.com>
  Date:   Wed Feb 3 09:42:42 2016 -0200
      Initial committ
#como o projeto local ainda não possuia referência ao projeto remoto, por não ter sido clonado inicialmente, associei o meu repositório remoto ao projeto locall
cmd> git remote add learngit-github https://github.com/fidelisfelipe/learngit.gittcmd> git remote -vvoutput>
learngit-github https://github.com/fidelisfelipe/learngit.git (fetch)learngit-github https://github.com/fidelisfelipe/learngit.git (push)
#após associado o remote, conferi que o local possuia um commit

cmd> git log

commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07
Author: Fidelis Guimaraes <Fidelis Guimaraes>
Date:   Wed Feb 3 09:38:52 2016 -0200

    primeiro commit - hello git
    
#fiz um merge com o commando pull
git pull learngit-github master

warning: no common commits
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/fidelisfelipe/learngit
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> learngit-github/master
Merge made by the 'recursive' strategy.
 README.md | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 README.md

#sabendo o hash do meu commit local, olhei as diferenças entre o que estava no master local(alterações recebidas pelo merge feito com o commando pull) e meu commit

git diff f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..88abc05
--- /dev/null
+++ b/README.md
@@ -0,0 +1,2 @@
+# learngit
+Estudo de conceitos e técnicas
   
#agora conferindo minha ordem cronológica, temos 3 commits, o 1º feito pelo repositório local, o 2º feito pelo repositório remoto após sua criação adicionando o Readme.md e o 3º ao realizar o pull(merge)

cmd> git log
output>
commit c0398607a931149f92f56765e7c38be97f4a11e6
Merge: f6b87bb dd81114
Author: Fidelis Guimaraes <Fidelis Guimaraes>
Date:   Wed Feb 3 09:48:58 2016 -0200

    Merge branch 'master' of https://github.com/fidelisfelipe/learngit

commit dd81114e97fe735fe5d90901c4e46bebb6818072
Author: Fidelis Felipe <atosfiel@gmail.com>
Date:   Wed Feb 3 09:42:42 2016 -0200

    Initial commit

commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07
Author: Fidelis Guimaraes <Fidelis Guimaraes>
Date:   Wed Feb 3 09:38:52 2016 -0200

    primeiro commit - hello git

#neste momento temos ramos distintos pois o primeiro criado foi meu ramo local, o segundo foi o ramo remoto, e em um dado momento esses ramos se encontraram mesclando seus conteúdos

cmd> git log --graph
output>
*   commit c0398607a931149f92f56765e7c38be97f4a11e6
|\  Merge: f6b87bb dd81114
| | Author: Fidelis Guimaraes <Fidelis Guimaraes>
| | Date:   Wed Feb 3 09:48:58 2016 -0200
| |
| |     Merge branch 'master' of https://github.com/fidelisfelipe/learngit
| |
| * commit dd81114e97fe735fe5d90901c4e46bebb6818072
|   Author: Fidelis Felipe <atosfiel@gmail.com>
|   Date:   Wed Feb 3 09:42:42 2016 -0200
|
|       Initial commit
|
* commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07
  Author: Fidelis Guimaraes <Fidelis Guimaraes>
  Date:   Wed Feb 3 09:38:52 2016 -0200

      primeiro commit - hello git

#enviei meu merge pronto agora para o servidor remoto
cmd> git push learngit-github master
output>
git: 'credential-cache' is not a git command. See 'git --help'.
Username for 'https://github.com': atosfiel@gmail.com
Password for 'https://atosfiel@gmail.com@github.com':
git: 'credential-cache' is not a git command. See 'git --help'.
Counting objects: 20, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (14/14), done.
Writing objects: 100% (20/20), 2.91 KiB | 0 bytes/s, done.
Total 20 (delta 2), reused 0 (delta 0)
To https://github.com/fidelisfelipe/learngit.git
   dd81114..c039860  master -> master

