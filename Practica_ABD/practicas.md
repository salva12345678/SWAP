# PRACTICAS ABD

## 4.Estructura  del  Almacenamiento  de  Oracle

1.Crear la carpeta /databases/app/ejercicios/data.

    mkdir /databases/app/ejercicios
    mkdir /databases/app/ejercicios/data

2.Crear los siguientes tablespaces permanentes, con un único fichero de datos de 50 M cada uno en la carpeta del paso 1:

    a) DATA con extensiones mínimas de 500K, incluyendo la inicial.

        create tablespace data datafile '/databases/app/ejercicios/data/data01.dbf' size 50 m minimum extent 500 k default storage (initial 500 k next 500k);

    b) RONLY de sólo lectura (realizar lo necesario). Intentar crear una tabla en dicho tablespace.

        create tablespace ronly datafile '/databases/app/ejercicios/datafiles/ronly01.dbf' size 10m minimum extent 500K default storage (initial 500k) offline;
        alter tablespace ronly online;
        alter tablespace ronly read only;
        create tablespace ronly  datafile '/databases/app/ejercicios/data/ronly01.dbf' size 50 m;

3.Ampliar a 100 M el tamaño de DATA01.dbf.

        alter database datafile '/databases/app/ejercicios/data/data01.dbf' resize 100 m;

4.Crear una tabla llamada prueba_data en DATA.

        create table prueba_data (a number) tablespace data;

5.Cambiar el nombre al datafile de RONLY;

        El profesor se ha creado una copia donde /databases/app/ejercicios/data/ de ronly01.dbf y la copia se llama ronly001.dbf.
        cp ronly01.dbf ronly001.dbf
        alter tablespace data offline;
        alter tablespace ronly rename datafile '/databases/app/ejercicios/data/ronly01.dbf' to '/data/app/ejercicios/data/ronly001.dbf';
        alter tablespace ronly online
        rm ronly001.dbf (en el directorio /databases/app/ejercicios/data)


6.Eliminar el tablespace RONLY y borrar sus ficheros.

        drop tablespace ronly; 
