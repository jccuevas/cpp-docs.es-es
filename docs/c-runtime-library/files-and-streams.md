---
title: "Archivos y secuencias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos [C++]"
  - "secuencias"
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos y secuencias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un programa se comunica con el entorno de destino leyendo y escribiendo los archivos.  Un archivo puede ser:  
  
-   Un conjunto de datos que se pueden leer y escribir repetidamente.  
  
-   Una secuencia de bytes generados por un programa \(como una canalización\).  
  
-   Una secuencia de bytes recibidos de o enviados a un dispositivo periférico.  
  
 Los dos últimos elementos son archivos interactivos.  Los archivos son los principales significa normalmente por qué interactuar con un programa.  Se manipula todas estas clases de archivos casi de la misma manera — llamando a funciones de biblioteca.  Se incluye el encabezado estándar STDIO.H para declarar la mayoría de estas funciones.  
  
 Para poder realizar muchas de las operaciones en un archivo, el archivo debe estar abierto.  Abrir un archivo se asocia a una secuencia, una estructura de datos dentro de la biblioteca de c estándar que se lustres sobre muchas diferencias entre archivos de clases diferentes.  La biblioteca mantiene el estado de cada secuencia en un objeto de FILE escrito.  
  
 El entorno de destino abra tres archivos antes de inicio del programa.  Puede abrir un archivo llamando a la función de biblioteca [fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md) con dos argumentos. \(Función de El `fopen` está desusado, utilice [fopen\_s, \_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) en su lugar.\) El primer argumento es un nombre de archivo.  El segundo argumento es la cadena de C\/C\+\+. que especifica:  
  
-   Si desea leer datos de un archivo o escribir datos él o ambos.  
  
-   Si desea generar nuevos contenido al archivo \(o crear un archivo si no existía previamente\) o dejar el contenido existentes en contexto.  
  
-   Si escribe en un archivo pueden modificar contenido existentes o deben anexar sólo bytes al final del archivo.  
  
-   Si desea manipular una secuencia de texto o una secuencia binaria.  
  
 Una vez que se abra el archivo correctamente, puede determinar si la secuencia está orientado a objetos byte \(un byte transmitir\) o orientado a objetos de ancho \(una secuencia elevado\).  Una secuencia se desata inicialmente.  Llamando a determinadas funciones para funcionar en la secuencia le crea el byte orientado a objetos, mientras que es seguro otras funciones se crean ancho orientado a objetos.  Una vez establecida, una secuencia mantiene su orientación hasta que sea una llamada a [fclose](../c-runtime-library/reference/fclose-fcloseall.md) o a [freopen](../c-runtime-library/reference/freopen-wfreopen.md).  
  
 © 1989\-2001 por P.J.  Plauger y Jim Brodie.  Todos los derechos reservados.  
  
## Vea también  
 [Secuencias binarias y de texto](../c-runtime-library/text-and-binary-streams.md)   
 [Secuencias anchas y de bytes](../c-runtime-library/byte-and-wide-streams.md)   
 [Controlar secuencias](../c-runtime-library/controlling-streams.md)   
 [Estados de secuencia](../c-runtime-library/stream-states.md)