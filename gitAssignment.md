# Git Assignment

**INDIVIDUAL**

**Entrega**: 23-Mar-21

Copie o arquivo em um repositorio que seja seu e coloque as respostas nas caixas abaixo
Abra uma issue nesse repositório aqui indicando o link para o arquivo no seu repo.

### Entenda o repositorio
Baixe o arquivo [handson.zip] (handson.zip) e descompacte-o
A pasta handson é um repositório git. Usando a linha de comando, altere o diretório para "handson/"


As caixas vazias
```

```
representam o conteúdo que você precisa preencher e postar em seu repositório privado

1. Descreva qual é a saída dos seguintes comandos
    -  `git branch` 
    -  `git checkout BRANCH_NAME` (USE THE NAME OF AN EXISTING BRANCH)
    -  `git log --decorate`

```
$ git branch
 feature-foo
 * master

R: Lista todas as branch e qual está sendo utilizada.

$ git checkout feature-foo 
Switched to branch 'feature-foo'

R: Troca de branch.

$ git log --decorate
commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Fri Aug 24 15:29:22 2018 -0700

    Adding header of method foo()

commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Fri Aug 24 15:27:16 2018 -0700

    Adding class A skeleton

commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Fri Aug 24 15:26:44 2018 -0700

    Creating all files (all empty)

R: Mostra os três últimos commits apresentando quem fez, quando fez e o nome do commit.
```

2. Tente usar `git log --graph --all`. O que acontece?
```
$ git log --graph --all
* commit f67f266cf420735187053f10d32e2c0f7cbc5a43 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:30:05 2018 -0700
| 
|     Adding class B skeleton
|   
| * commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Fri Aug 24 15:29:22 2018 -0700
|   
|       Adding header of method foo()
| 
* commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:27:16 2018 -0700
| 
|     Adding class A skeleton
| 
* commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Fri Aug 24 15:26:44 2018 -0700
  
      Creating all files (all empty)

R: Apresenta os commits e retorna informações dos commits antecessores.
```

3. Use `git diff BRANCH_NAME`  para ver as diferenças de um ramo e do ramo atual.
   Sumarize as diferenças do master e do outro ramo.

```
 git branch
* feature-foo
  master


$ git diff master
diff --git a/A.java b/A.java
index 3ea227e..674b8ce 100644
--- a/A.java
+++ b/A.java
@@ -1,4 +1,7 @@
 public class A {
-
+   
+   public void foo() {
+   
+   }
 
 }
diff --git a/B.java b/B.java
index ae64e6b..e69de29 100644
--- a/B.java
+++ b/B.java
@@ -1,4 +0,0 @@
-public class B {
-
-
-}

R: Então foi comparado o ramo 'feature-foo' com a 'master'. Primeiramente, podemos notar que foi adicionado um método na classe A. Por fim, a última diferença que podemos ver é que no ramo master foi escrito a classe B.

```

4. Escreva uma sequencia de comandos para mesclar o ramo não-master no `master`

```
$ git checkout master
Switched to branch 'master'

$ git merge feature-foo 
Merge made by the 'recursive' strategy.
 A.java | 5 ++++-
 1 file changed, 4 insertions(+), 1 deletion(-)
```


5. Escreva um comando (ou sequência) para (i) criar um novo ramo chamado `math` (do` master`)
e (ii) mudar para este ramo

```
$ git branch
  feature-foo
* master

$ git checkout -b math
Switched to a new branch 'math'

```
   
6. Edite B.java adicionando o código abaixo ao conteúdo do arquivo
```java
System.out.println("I know math, look:")
System.out.println(2+2)
```

7. Escreva o comando (ou sequencia) para realizar o commit de suas mudanças
```
$ git commit -a -m 'Adicionando prints'
[math 0de7862] Adicionando prints
 1 file changed, 2 insertions(+), 2 deletions(-)

R: Se não foi criado nenhum arquivo, caso contrário são os comandos abaixo.

$ git add .
$ git commit -m 'Adicionando prints'
```

8. Volte para o branch `master` e mude B.java adicionando o seguinte código-fonte (confirme sua mudança para` master`):
```java
System.out.println("Hello World")
```

9. Escreva uma sequência de comando para mesclar o branch `math` em` master` e descreva o que aconteceu
```
$ git commit -a -m 'Adicionando prints'
[master 4379fac] Adicionando prints
 1 file changed, 1 insertion(+), 2 deletions(-)

$ git merge math
Mesclagem automática de B.java
CONFLITO (conteúdo): conflito de mesclagem em B.java
Automatic merge failed; fix conflicts and then commit the result.

```
   
10. Escreva um conjunto de comandos para abortar a mesclagem
```
$ git merge --abort
```
   
11. Agora repita o item 9, mas prossiga com a mesclagem manual (Editando B.java). Todas as funções implementadas são necessárias. Explique o seu procedimento
```
$ git merge --abort

$ git merge math
Mesclagem automática de B.java
CONFLITO (conteúdo): conflito de mesclagem em B.java
Automatic merge failed; fix conflicts and then commit the result.

$ git status
No ramo master
Você tem caminhos não mesclados.
  (fixar conflitos e executar "git commit")
  (use "git merge --abort" to abort the merge)

Caminhos não mesclados:
  (usar "git add <arquivo>..." para marcar resolução)
	ambos modificados:   B.java

nenhuma modificação adicionada à submissão (utilize "git add" e/ou "git commit -a")

$ pico B.java
public class B {
<<<<<<< HEAD
        System.out.println("Hello World")

=======
        System.out.println("I know math, look:")
        System.out.println(2+2)
        System.out.println("Hello World")
>>>>>>> math
}

$ echo 'Depois de arrumado...'
$ cat B.java
public class B {
        System.out.println("Hello World")
}

$ git commit -a -m 'Arrumando conflito'
[master 0579ed7] Arrumando conflito

```

12. Escreva um comando (ou conjunto de comandos) para prosseguir com a mesclagem e atualizar o branch `master`
```
$ git push
Username for 'https://github.com': xaaaandao
Password for 'https://xaaaandao@github.com': 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 2.97 KiB | 2.97 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/xaaaandao/gitAssignment.git
   38c6e6d..e97b47f  main -> main
```




