# PRACTICAS ABD.

## 4.Estructura  del  Almacenamiento  de  Oracle.

## Tablespaces

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

        drop tablespace data including contents;
        drop tablespace ronly;
        Hay que borrar manualmente los ficheros al final


## Segmentos, Extensiones y Bloques

1.Identificar los distintos tipos de segmentos que hay en la BD.

        select distinct segment_type from dba_segments;
        select segment_name ,extents ,max_entents from dba_segments;
        select extents,max_entents,extents/max_entents from dba_extents where extents =(select max(extents) from dba_segments);
        select max(extents) from dba_segments;

2.Averiguar qué segmentos tienen ocupadas más del 30% de sus extensiones.

        select segment_name from  dba_segments where extents > 0.3*max_entents;

3.¿Qué ficheros contienen datos de la tabla prueba_data? (dba_extents-dba_data_files).

        select segment_name, segment_type, file_name from dba_extents, dba_data_files where dba_extents.file_id=dba_data_files.file_id and segment_name='EMP';
        describe dba_extents;
        select segment_name from dba_segments where tablespace_name='DATA';

## Usuario

1.Crear el usuario Bob con password ALONG, asegurando que no utilice espacio en SYSTEM y que no sobrepase 1M en el tablespace USERS. Dejar que se conecte.

        create user bob identified by ALONG default tablespace users quota 1 m on users;
        grant connect to bob;

        En otra terminal:
              sqlplus bob@oradba

        alter users bob quota 0 m on system;      

2.Crear el usuario Kay con password Mary asegurando que los objetos y el espacio temporal necesarios no sean de SYSTEM. Asignar cuota ilimitada en el tb de datos.

        create user kay identified by Mary default tablespace users quota unlimited on users quota 0 m on system;


3.Copiar la tabla EMP del usuario SCOTT en la cuenta de Kay.

        create user SCOTT identified by tiger default tablespace users temporary tablespace temp quota unlimited on system;
        grant connect ,resource to scott;
        create table kay.emp as select * from scott.emp;

4.Mostar la información sobre Bob y Kay y sobre sus límites de espacio en los tablespaces correspondientes.

        select username, tablespace_name, max_bytes from dba_ts_quotas where username in ('BOB', 'KAY');
