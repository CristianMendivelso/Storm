# Word-Count Storm

Contador de Palabras Obtenidas de un archivo de texto Utilizando la Herramienta Apache Storm Basado en https://github.com/khajaasmath786/StormTutorial y utlizando las caracterísitcas de Streaming del mismo.

Este es un repositorio que se utilizará para un proyecto de investigación de la Escuela Colombiana de Ingeniería Julio Garavito

Se ha actualizado el proyecto para ser usado en apache storm 1.1.0, y se ha ampliado para ser usado en modo cluster.

Para Ejecutar Esta Aplicación Es Necesario:

Clonar el repositorio Ir a la carpeta del repositorio y ejecutar el comando : mvn clean package assembly:single En el nodo nimbus, ir a la carpeta de apache storm y bin/storm jar [ruta al target]/[nombre del archivo jar con dependencias].jar com.mycompany.yahoostorm.HelloStorm word-count

Para cambiar la cantidad de trabajadores solamente es editar la línea config.setNumWorkers(3); en HelloStorm.java

Para Correrlo En Modo Local

Eliminar estas dos filas del archivo HelloStorm.java
    config.setNumWorkers(3);
    StormSubmitter.submitTopology("word-counter", config, builder.createTopology());
y reemplazarlas por
    LocalCluster cluster = new LocalCluster();
    cluster.submitTopology("HelloStorm", config, builder.createTopology());
    Thread.sleep(10000);
    cluster.shutdown();
 
En caso de no ejecutar elimine en el archivo pom.xml la línea
   scope
de la dependencia de apache storm
