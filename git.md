# Git 
### Git es un software de control de versiones gratis y de código abierto. Fue creado por Linus Torvalds en 2005. Esta herramienta es un sistema de control de versiones que fue inicialmente desarrollado para trabajar con varios desarrolladores en el núcleo de Linux.
#### **Algunos Comandos importantes**
git status <br>
git status -s <br>
git commit -m "lo_que_modificamos" <br>
git log <br>
git log --onefile <br>
git diff <br>
git diff --staged <br>
git mv nombreviejo nombrenuevo(cambio de nombre) <br>
git init (para iniciar) <br>
git config --global user.name <br>
git config --global user.email <br>
git config --global core.editor "code --wait" <br>
git config --global -e(para probar el edito) <br>
git config --global core.autocrlf true(win) // input(mac, linux) <br>
el archivo .gitignore sirve para poner todos los archivos y carpetas con no queramos que se sincronizen con git <br>
git restore --staged nombre archivo(se utiliza para devolverlo un paso atras para luego descartar el cambio<br>
git restore nombre del mismo archivo (elimina los cambio por completo)<br>
git branch (muestra la rama que estamos)<br>
git checkout -b (nombre de la rama)<br>
git marge nombre rama creada anteriormente(para que el marge se realice en la rama main tenemos que estar sobre ella y llamar a rama b para que unan)<br>
[Volver](README.md)