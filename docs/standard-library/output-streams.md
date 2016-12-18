---
title: "Flujos de salida | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flujos de salida"
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
caps.latest.revision: 12
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Flujos de salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto de secuencia de salida es un destino para los bytes.  Las tres clases más importantes del flujo de salida son `ostream`, `ofstream`, y `ostringstream`.  
  
 La clase de `ostream` , a través de la clase derivada `basic_ostream`, admite los objetos de secuencia predefinidos:  
  
-   salida estándar de`cout`  
  
-   error típico de`cerr`con el almacenamiento en búfer limitado  
  
-   `clog` similar a `cerr` pero con el almacenamiento en búfer completo  
  
 Los objetos se crean casi de `ostream`; los objetos predefinidos se utilizan normalmente.  En algunos casos, puede reasignar objetos predefinidos después de inicio del programa.  La clase de `ostream` , que se puede configurar para la operación almacenado en búfer o inseparada, es mejor para la salida secuencial del modo de texto.  Toda la funcionalidad de la clase base, `ios`, se incluye en `ostream`.  Si crea un objeto de clase `ostream`, debe especificar un objeto de `streambuf` al constructor.  
  
 La clase de `ofstream` admite el resultado del archivo de disco.  Si necesita un disco envía solo, cree un objeto de la clase `ofstream`.  Puede especificar si los objetos de `ofstream` aceptan el binario o datos del modo de texto al construir el objeto de `ofstream` o al llamar a la función miembro de `open` del objeto.  Muchas opciones de formato y funciones miembro se aplican a los objetos de `ofstream` , y toda la funcionalidad de las clases base `ios` y `ostream` va incluida.  
  
 Si especifica un nombre de archivo en el constructor, ese archivo se abre automáticamente cuando se construye el objeto.  Si no, puede utilizar la función miembro de `open` después de invocar el constructor predeterminado.  
  
 Como la función `sprintf_s`en tiempo de ejecución, la clase de `ostringstream` admite la salida de las cadenas de en\- memoria.  Para crear una cadena en memoria utilizando el formato de la secuencia de E\/S, cree un objeto de la clase `ostringstream`.  
  
## En esta sección  
 [Construir objetos de flujo de salida](../standard-library/constructing-output-stream-objects.md)  
  
 [Usar operadores de inserción y controlar el formato](../standard-library/using-insertion-operators-and-controlling-format.md)  
  
 [Funciones de miembro de flujo de archivos de salida](../standard-library/output-file-stream-member-functions.md)  
  
 [Efectos del almacenamiento en búfer](../standard-library/effects-of-buffering.md)  
  
 [Archivos de salida binarios](../standard-library/binary-output-files.md)  
  
 [Sobrecargar el operador \<\< para las clases propias](../standard-library/overloading-the-output-operator-for-your-own-classes.md)  
  
 [Escribir manipuladores propios sin argumentos](../standard-library/writing-your-own-manipulators-without-arguments.md)  
  
## Vea también  
 [miembros de \<ostream\>](http://msdn.microsoft.com/es-es/a5afd034-0e3c-41ee-bbd7-468d9188da1d)   
 [ofstream](../Topic/ofstream.md)   
 [ostringstream](../Topic/ostringstream.md)   
 [miembros de basic\_ostream](http://msdn.microsoft.com/es-es/82e5cc91-7c0c-4950-a8ce-ac779cfbbd93)   
 [Programación con iostream](../standard-library/iostream-programming.md)