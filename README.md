# learngit
Estudo de conceitos e técnicas

##projeto criado primeiro que o repositório

cmd> git init<br>
cmd> git add. <br>
cmd> git commit -m"primeiro commit - hello git"<br>
output><br>
<pre><code>
<br>
[master (root-commit) f6b87bb] primeiro commit - hello git<br>
warning: LF will be replaced by CRLF in .gitignore.<br>
The file will have its original line endings in your working directory.<br>
 12 files changed, 118 insertions(+)<br>
 create mode 100644 .classpath<br>
 create mode 100644 .gitignore<br>
 create mode 100644 .project<br>
 create mode 100644 .settings/.jsdtscope<br>
 create mode 100644 .settings/org.eclipse.jdt.core.prefs<br>
 create mode 100644 .settings/org.eclipse.wst.common.component<br>
 create mode 100644 .settings/org.eclipse.wst.common.project.facet.core.xml<br>
 create mode 100644 .settings/org.eclipse.wst.jsdt.ui.superType.container<br>
 create mode 100644 .settings/org.eclipse.wst.jsdt.ui.superType.name<br>
 create mode 100644 WebContent/META-INF/MANIFEST.MF<br>
 create mode 100644 WebContent/WEB-INF/web.xml<br>
 create mode 100644 WebContent/index.html<br>
<br>
</code></pre>

###conferi o meu commit

cmd>git log<br>
output><br>
<pre><code>
* commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d0<br>
<br>
  Author: Fidelis Guimaraes <Fidelis Guimaraes><br>
<br>
  Date:   Wed Feb 3 09:38:52 2016 -020<br>
<br>
      primeiro commit - hello git<br>
</code></pre>

###depois foi criado o repositório remoto no git com um arquivo Readme.md

<pre><code>
* commit dd81114e97fe735fe5d90901c4e46bebb681807<br>
<br>
  Author: Fidelis Felipe <atosfiel@gmail.com><br>
<br>
  Date:   Wed Feb 3 09:42:42 2016 -020<br>
<br>
        Initial commit<br>
</code></pre>

###como o projeto local ainda não possuia referência ao projeto remoto, por não ter sido clonado inicialmente, associei o meu repositório remoto ao projeto local

cmd> git remote add learngit-github https://github.com/fidelisfelipe/learngit.git<br>
cmd> git remote -v<br>
output><br>
<pre><code>
learngit-github https://github.com/fidelisfelipe/learngit.git (fetch)<br>
learngit-github https://github.com/fidelisfelipe/learngit.git (push)<br>
</code></pre>

###após associado o remote, conferi que o local possuia um commit

cmd> git log<br>
output>
<pre><code>
<br>
* commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07<br>
Author: Fidelis Guimaraes <Fidelis Guimaraes><br>
Date:   Wed Feb 3 09:38:52 2016 -0200<br>
<br>
    primeiro commit - hello git<br>
</code></pre>
  
###fiz um merge com o commando pull
git pull learngit-github master<br>
<br>
warning: no common commits<br>
remote: Counting objects: 3, done.<br>
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0<br>
Unpacking objects: 100% (3/3), done.<br>
From https://github.com/fidelisfelipe/learngit<br>
 * branch            master     -> FETCH_HEAD<br>
 * [new branch]      master     -> learngit-github/master<br>
Merge made by the 'recursive' strategy.<br>
 README.md | 2 ++<br>
 1 file changed, 2 insertions(+)<br>
 create mode 100644 README.md<br>

</code></pre>

###sabendo o hash do meu commit local, olhei as diferenças entre o que estava no master local(alterações recebidas pelo merge feito com o commando pull) e meu commit

git diff f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07<br>
output>
<pre><code>
<br>
diff --git a/README.md b/README.md<br>
new file mode 100644<br>
index 0000000..88abc05<br>
--- /dev/null<br>
+++ b/README.md<br>
@@ -0,0 +1,2 @@<br>
+# learngit<br>
+Estudo de conceitos e técnicas<br>
</code></pre>
   
###agora conferindo minha ordem cronológica, temos 3 commits, o 1º feito pelo repositório local, o 2º feito pelo repositório remoto após sua criação adicionando o Readme.md e o 3º ao realizar o pull(merge)

cmd> git log<br>
output><br>
<pre><code>
* commit c0398607a931149f92f56765e7c38be97f4a11e6<br>
Merge: f6b87bb dd81114<br>
Author: Fidelis Guimaraes <Fidelis Guimaraes><br>
Date:   Wed Feb 3 09:48:58 2016 -0200<br>
<br>
    Merge branch 'master' of https://github.com/fidelisfelipe/learngit<br>
<br>
* commit dd81114e97fe735fe5d90901c4e46bebb6818072<br>
Author: Fidelis Felipe <atosfiel@gmail.com><br>
Date:   Wed Feb 3 09:42:42 2016 -0200<br>
<br>
    Initial commit<br>
<br>
* commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07<br>
Author: Fidelis Guimaraes <Fidelis Guimaraes><br>
Date:   Wed Feb 3 09:38:52 2016 -0200<br>
<br>
    primeiro commit - hello git<br>
<br>

</code></pre>

###neste momento temos ramos distintos pois o primeiro criado foi meu ramo local, o segundo foi o ramo remoto, e em um dado momento esses ramos se encontraram mesclando seus conteúdos

cmd> git log --graph<br>
output>
<pre><code>
*   commit c0398607a931149f92f56765e7c38be97f4a11e6<br>
|\  Merge: f6b87bb dd81114<br>
| | Author: Fidelis Guimaraes <Fidelis Guimaraes><br>
| | Date:   Wed Feb 3 09:48:58 2016 -0200<br>
| |<br>
| |     Merge branch 'master' of https://github.com/fidelisfelipe/learngit<br>
| |<br>
| * commit dd81114e97fe735fe5d90901c4e46bebb6818072<br>
|   Author: Fidelis Felipe <atosfiel@gmail.com><br>
|   Date:   Wed Feb 3 09:42:42 2016 -0200<br>
|<br>
|       Initial commit<br>
|<br>
* commit f6b87bb73dae8a9e6a5f2afdd13fb550cc4e0d07<br>
  Author: Fidelis Guimaraes <Fidelis Guimaraes><br>
  Date:   Wed Feb 3 09:38:52 2016 -0200<br>
<br>
      primeiro commit - hello git<br>
</code></pre>

###enviei meu merge pronto agora para o servidor remoto

cmd> git push learngit-github master<br>
output><br>
<pre><code>
git: 'credential-cache' is not a git command. See 'git --help'.<br>
Username for 'https://github.com': atosfiel@gmail.com<br>
Password for 'https://atosfiel@gmail.com@github.com':<br>
git: 'credential-cache' is not a git command. See 'git --help'.<br>
Counting objects: 20, done.<br>
Delta compression using up to 4 threads.<br>
Compressing objects: 100% (14/14), done.<br>
Writing objects: 100% (20/20), 2.91 KiB | 0 bytes/s, done.<br>
Total 20 (delta 2), reused 0 (delta 0)<br>
To https://github.com/fidelisfelipe/learngit.git<br>
   dd81114..c039860  master -> master<br>
</code></pre>

###voltei ao passado e estou atualizando o arquivo que havia esquecido
###utilizei o git stash que salvou meu readme sem commitar
###com git stash list consigo ver o id do meu stash (estado salvo sem commit)
###defini que iria para o ultimo salvamento do readme que era o commit d250278, então usei git checkout d250278
output><br>
<pre><code>HEAD is now at d250278... atualizando Readme.md</code></pre>
<br>
#Voltando um commit antigo sem commitar o presente

##entao agora vou fazer uma alteração em um arquivo(poderiam ser vários), mas não quero fazer um commit dele, mas também não quero perder minha alteração, para isso vou fazer um commit temporário, voltar ao meu commit antigo, depois voltar ao presente e commitar o arquivo alterado...

###vou visualizar de uma forma diferente meu estado atual do branch
cmd>git log --graph --oneline --decorate<br>
output><br>
<pre><code>
* 4db3b95 (HEAD -> master, learngit-github/master) mudança de arquivo de pacote
* d250278 atualizando Readme.md
* 479db06 atualizando Readme.md
*   c039860 Merge branch 'master' of https://github.com/fidelisfelipe/learngit
|\
| * dd81114 Initial commit
* f6b87bb primeiro commit - hello git
</code></pre>

###ver o status dele também
cmd>git status<br>
<pre><code>

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

</code></pre>

###não está adicionado meu Readme com as alterações

###utilizei o git stash para salvar o estado
###fiz um checkout para o commit que eu queria(ultima alteração ate o momento do readme)
###alterei o readme
###apliquei o que não estava salvo anteriormente com git stash apply stash@{0}
###agora eu adicionei novamente o readme atualizado