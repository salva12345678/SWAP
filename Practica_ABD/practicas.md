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

4.Crear una tabla llamada prueba_data en DATA.

5.Cambiar el nombre al datafile de RONLY;

6.Eliminar el tablespace RONLY y borrar sus ficheros.