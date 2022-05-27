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
5. man
Para buscar el manual en treminal indicar, por ejemplo para buscar opciones para la funcion ls:
```bash
man ls
```
6.rm
```bash
rm <file_name>
```
remove, elimina ficheros, no directorios
```bash
rm <nombre_carpeta> -r
```
rm -r elimina la carpeta con todos los ficheros que hay dentro. Se elimina de forma recurisva (-r) todos los elementos que hay dentro del fichero hasta que queda vacia, si la carpeta esta vacia no elimina la carpeta
6.rmdir
```bash
rmdir
```
remove directory, elimina  directorios sin ficheros en ellos
7.mkdir
```bash
mkdir <nombre_carpeta>
```
se crea carpeta en el directorio donde nos encontramos
8.touch
```bash
touch <nombre_fichero.tipo_fichero>
```
Crea fichero en el directorio donde estamos, hay que especificar tipo

####Rutas
rutas relativas: no  mostramos  todos  los directorios,  ejemplo ./carpeta_3, no muestra todos los directorios superiores a carpeta_3, se resumen con ./

rutas absolutas: camino con  todos los directorios donde nos encontramos, la ruta empieza con /, se  puede  ver con  comando 

9.pwd
```bash
pwd
```
Muestra ruta

10.cat
```bash
cat <nombre_fichero>
cat <nombre_fichero> | grep <texto>
```
muestra contenido del fichero, grep imprime las lineas que continene texto

11.nano
```bash
nano <nombre_fichero>
```
Abre editor de texto del fichero especificado

12.mv
```bash
mv <name>  <where>
```
Mover ficheros o directorios
```bash
mv <antiguo_nombre> <nuevo_nombre>
```
mv tmabien sirve  para  cambiar nombre de ficheros oo directorios

Los ficheros que empiezan con . son ocultos

####GIT:
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
####Otros comandos bash
```bash
find . -type f -printf "f\t%p\t%u\t%g\t%m\n" | column -t #te imprime todos los ficheros encontrados con su nombre (f), directorio (p = path), user, group y permisos (m). Al poner column -t the tabula correctamente la impresion para hacer más facil la visualizacion
find . name <file_name> | xargs cat #xargs se usa para dado un archivo o un grupo de archivos encontrados mediante comandos, ejecutar otro comando, en este caso buscamos los ficheros con un nombre concreto y luego aplicamos un cat (leer)
find . -type f | xargs grep "<word>" # en este caos buscamos todos los archivos tipo fichero y le aplicamos un grep, es decir va a imprimir todas las lienas que contengan "<word>" de todos los archivos tipo file encontrados.
ls -l #muestra los permisos para cada archivo
lsattr #muestra permisos especiales
```

###Permisos
Los permisos son grupos de tres variables para grupo, users y others. Marcan quien puede leer, escribir y ejecutar cada archivo. Se vee como rwx rwx rwx, si se ve la letra significa que el usuario o gurpo tiene el privilegio, si no tiene se vee un -
Los privilegios se pueden convertir a decimal, ejemplo
Privilegio rw-r---w-
110 100 010
6 4 2
el privielgio rw-r---w- es el 642
Privilegio rwxrw-r--
111 110 100
7 6 4
El privilegio rwxrw-r-- es el 764
```bash
chmod <decimal_number> <file_name> # con el chmod cambiamos los permisos del file_name, los nuevos permisos vendran indicados por el decimal_number segun la explicacion anterior
chmod o+w,g-r <file_name> #tambien se puede trabajar con letras, en este caso estamos dando el permiso de w a otros y quitando el premiso read a grupo
chattr -i -V <file_name> #modifica permisos especiales !, en este caso estamos quitando el permiso i, y usamos el -V para que nos imprima los permisos del fichero actualizados, el -V es para visualizar simplemente.
```
###Más comandos bash
```bash
hexeditor <file_name> #vemos arxivo en hexadiecimal
file <file_name> #vemos el tipo de archivo
time <comand> #hace el comando y al final muestra el tiempo de computo de la accion realizada
cat $(find . -name <file_name>) #hace un cat al resulado del find, el $() da el directorio de los archivos encontrados.
find . -type f -readable -writable ! -executable -size 1033c# buscamos un archivo tipo fichero que sera leible, que se pueda escribir y que no sea ejecutable (si ponemos una exlamacion al inicio en bash negamos accion) y de un tamaño de 1033 bytes
#si ponemos un cat $(<previous_comand>) nos lee el archivo que encuentre
#hace lo mismo si a <previous_comand> | xargs cat
```
Existen metodos para limpiar el resultado de leer un archivo, borrar saltos de linea inecesarios, tabuladores etc. Ejemolos:
```bash
<previous_comand> | xargs cat | xargs 
| head -n 1 #devuelve la primera linea
| head -n 2 #devuelve primera y segunda linea
| tail -n 2 #devuelve las dos ultimas lineas
| awk 'NR==2' #devuelve la linea dos
#si añadimos comando sed permite hacer modificaciones a la linea
| sed 's/root/noroot/' #si añadimos esto al final de un comando de lectura se substituira (s) la primera palabra root encontrada pro noroot
| sed 's/root/noroot/g' #si añadimos g al final se substituyen todas las palabras root de la impresion por noroot
| grep '^<word>' #si hacemos un grep normal nos devuelven todas las lineas donde aparce <word>, si añadimos ^al principio especificamos que la linea debe empezar <word>
| sed 's/^ *//' #en este casos substituimos todas las lineas que empiezan por espacio seguidas de qualquier cosa (*) por nada, es decir, se eliminan
| grep <word$> #especificamos que queremos que la linea se termine por word
| grep <^word$> -n #nos devuelbe la linea que empieze y termine por word, es decir la linea que sea word y con (-n) nos indica en que linea se encuentra
 find / -user bandit7 -group bandit6 -size 33c #cuando hacemos find . buscamos los archivos desde el directorio donde estamos hacia abajo, con find / buscamos des de raiz, en este caso buscamos un fichero con el ususario bandit7, grupo bandit6 y tamaño 33 bytes
 #si hacemos esta accion probalemente dara errores de permisos, si queremos ver solo los comandso exitosos hay que añadir 2>/dev/null al final, esto driecciona (>) todos los errores (2 'numero interno de bash para referirse a erroes') a la carpeta /dev/null que es una especie de ajugero negro tipo "basura"
 ```
 Esto puede tener muchas utilidades, si iniciamos un programa por terminal, muchas vees nos va mostrando todos los cmandos de las acciones del programa, si hacemos:
 ```bash
 firefox > /dev/null #inicializamos firefox y mandamos todo el flow del programa al null, de este modo mantenemos la terminal limpia
 firefox > /dev/null 2>&1 #con la accion anterior los erroes si se mostravan en terminal, de este modo convertimos (>) los erroes (2) a formato stdim (&1) y de este modo tambien son redireccionados a /dev/null
firefox > /dev/null 2>&1 & # si añadimos & al final ponemos la accion en segundo plano
'''
Cuando abrimos procesos des de terminal, por ejemplo ejecutamos programas, estos estan linkados a la terminal, si se cierra terminal se cierra el programa, para independizar usamos comando:
```bash
disown -a #si nos diche job not found usamos solo disown
disown
```

```bash
cat data.txt | wc -l #contabiliza todas las lineas en el fichero data.txt
cat data.txt | wc -c #contabiliza los caracteres en el fichero data.txt
'''
Para buscar lineas que contengan cierta palabra tenemos diferentes ocpciones, Ejemolo linea:millionth  dasfkhguieakjhdaiu:
```bash
cat data.txt | grep "millionth" #lee todo el fichero i imprime las lineas que contengan millionth
grep "millionth" data.txt #misma accion que antes pero mas eficiente ya que nos ahorramos el cat, si hacemos un time veremos que es mas rapido
awk "/millionth/" data.txt #devuelve toda la linea
awk "/millionth/" data.txt | awk '{print $1} # devuelve millionth
awk "/millionth/" data.txt | awk '{print $2} # devuelve dasfkhguieakjhdaiu
awk "/millionth/" data.txt | awk 'NF{print $NF} # devuelve el ultimo argumento de la linea
awk "/millionth/" data.txt | awk 'NF{print $NF} | rev # devuelve el ultimo argumento de la linea revertido.
```
Otros ejemplos:
```bash
echo "Hola     que tal" | cut ' ' -f 1 #echo imprime el texto, con cut -f lo que hacemos es filtrar hasta el primer espacio i que nos devuelva el primer campo de la izquierda, por lo tanto esto devuelve Hola. Si ponemos -f 3 como entre el 3 espacio i el espacio anterior no devolveria nada

Como filtrar cadenas que ocurren una sola vez:
```bash
cat data.txt | uniq -u #solo elimina las lineas que ocurren mas de una vez si estan una al lado de la otra, para solucionar:
cat data.txt | sort | uniq -u #ordena todas las lineas, por tanto si hay repetidas estaran una detras de otra y luego con el uniq las eliminamos
# tmb existe comando unique que toma directamente linea unica
'''

### Util
```bash
<comand> !$ #!$ referencia el comando al ultimo argumento de comando que se ha ejecutado, ejemlo:
touch data.txt
nono !$ #abre data.txt
```

###Bucles en bash
'''bash
contador=1 #no se pueden dejar espacios
while read line; do #bucle bash
  echo "linea $contador: $line #accion a realizar dentro del bucle, con $ llamos a variables
  let contador+=1 #con let incrementamos contador
 done < data.txt #ejecutamos bucle en fichero data.txt
 '''
Si en lugar de un fichero si quiere hacer un bucle de un comando:
```bash
strings data.txt | grep "===" | while read line; do echo $line; done #lista todas las lineas del data.txt que contengan ===
```
```bash
contador=1; strings data.txt | grep "===" | while read line; do echo "Linea $contador: $line"; let contador+=1; done #lista todas las lineas que contengan === con numero de linea delante 
```

###Otros
Pagina para practicar comandos de terminal:
https://overthewire.org/wargames/bandit/bandit0.htmlc
Video para  scriptin:
Scriptin en Bash para principiantes #1 s4evitar

Buscar significado fetch y push relativos a origen ficheros git
