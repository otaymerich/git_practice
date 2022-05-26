### Comandos terminal:

1. ls: lista los ficheros en el wd
```bash
ls
```
Puede recivir elementos opcionales
```bash
ls -a
```
lista los niveles de directorios
```bash
ls nombre_fichero
```
Lista los ficheros en el wd de nombre_fichero
```bash
ls nombre_fichero -a == ls -a nombre_ficher0
```
se puede intercanviar orden de acciones

```bash
ls inico_nombre_fichero + tab
ls + tab + tab
```
autocompleta nombre fichero
recomienda ficheros disponibles


2. clear
3. pwd: da la ruta de la carpeta donde estamos situados
4. cd: change directory, para moverse dentro de las carpetas
```bash
cd lacarpeta_nueva
```
Para moverse hacia la  carpeta suuperior:
```bash
cd ..
```
Recordatorio: se pueden ver los niveles de la carpeta donde estamos con ls -a

Manual de todas las funciones que existen en  la  terminal:

https://www.bell-labs.com/usr/dmr/www/1stEdman.html

Para buscar el manual en treminal indicar, por ejemplo para buscar opciones para la funcion ls:
```bash
man ls
```
```bash
rm
```
remove, elimina ficheros, no directorios
```bash
rmdir
```
remove directory, elimina  directorios sin ficheros en ellos
```bash
mkdir <nombre_carpeta>
```
se crea carpeta en el directorio donde nos encontramos
```bash
touch <nombre_fichero.tipo_fichero>
```
Crea fichero en el directorio donde estamos, hay que especificar tipo
```bash
rm <nombre_carpeta> -r
```
rm -r elimina la carpeta con todos los ficheros que hay dentro. Se elimina de forma recurisva (-r) todos los elementos que hay dentro del fichero hasta que queda vacia




rutas relativas: no  mostramos  todos  los directorios,  ejemplo ./carpeta_3, no muestra todos los directorios superiores a carpeta_3, se resumen con ./

rutas absolutas: camino con  todos los directorios donde nos encontramos, la ruta empieza con /, se  puede  ver con  comando 
```bash
pwd
```
```bash
cat <nombre_fichero>
cat <nombre_fichero> | grep <texto>
```
muestra contenido del fichero, grep imprime las lineas que continene texto

```bash
nano <nombre_fichero>
```
Abre editor de texto del fichero especificado
```bash
mv <name>  <where>
```
Mover ficheros o directorios
```bash
mv <antiguo_nombre> <nuevo_nombre>
```
mv tmabien sirve  para  cambiar nombre de ficheros oo directorios

Los ficheros que empiezan con . son ocultos

GIT:
```bash
git add <ficheros> #anyadimos ficheros a git pero no los subimos
git commit -m "<mensaje>"#confirmamos la subida de todos los archivos add, anadimos punto en rama temporal de git
git push origin <nombre rama> #subimos a nube
git status #vemos estado y rama donde estamos situados
git branch <name> #crea rama
```
Si se quiere subir un fichero modificado tambien se usa add

Cuando hay una modificacion en un fichero hay que volver a anyadir, commit y push origin

Para unir ramas hay que ubicarse en la rama donde queremos unir, es decir, la rama que recibe el merge
```bash
git checkout master #nos ubicamos a la rama donde queremos mergear
git merge develop #rama que queremos mergear
```
```bash
git log #indica todos los commits que se han echo, con un identificador, quien lo ha echo, nombre, fecha y hora.
```
se puede viajar temporalmente: si hacemos:
```bash
git checkout <indicador> #obtenemos identificador con git log
```

Para tener ficheros que no queremos que subamos en git se crea carpeta .gitignore donde anadiremos por lineas todos los ficheros y carpetas que no queremos que se suban

```bash
git echo <whatever> #hace un print
git echo <whatever> > <nombre_fichero> #escribe whatever en nombre_fichero, borra todo lo que habia
git echo <whatever> >> <nombre_fichero> #anade  whatever done estaba por ultima vez el cursor en nombre_fichero
```


Pagina para practicar comandos de terminal:
https://overthewire.org/wargames/bandit/bandit0.htmlc
Video para  scriptin:
Scriptin en Bash para principiantes #1 s4evitar

Buscar significado fetch y push relativos a origen ficheros git