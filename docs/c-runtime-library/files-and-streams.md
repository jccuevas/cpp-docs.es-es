---
title: Archivos y secuencias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a93fc1aa0f3108d4897a45b9014970afab220439
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="files-and-streams"></a>Archivos y secuencias
Un programa se comunica con el entorno de destino al leer y escribir archivos. Un archivo puede ser:  
  
-   Un conjunto de datos que se puede leer y en el que se puede escribir repetidamente.  
  
-   Una secuencia de bytes generada por un programa (por ejemplo, una canalización).  
  
-   Una secuencia de bytes recibida de un dispositivo periférico o enviada a dicho dispositivo.  
  
 Los dos últimos elementos son archivos interactivos. Los archivos suelen ser el medio principal por el que se va a interactuar con un programa. Puede manipular todos estos tipos de archivos más o menos de la misma forma con una llamada a las funciones de la biblioteca. Incluya el encabezado estándar STDIO.H para declarar la mayoría de estas funciones.  
  
 Para poder realizar muchas de las operaciones en un archivo, es necesario abrirlo. Al abrir un archivo este se asocia con una secuencia, una estructura de datos dentro de la biblioteca estándar de C que pasa por alto muchas diferencias entre archivos de varios tipos. La biblioteca mantiene el estado de cada secuencia en un objeto de tipo de ARCHIVO.  
  
 El entorno de destino abre tres archivos antes de iniciar el programa. Puede abrir un archivo mediante una llamada a la función de la biblioteca [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) con dos argumentos. (La función `fopen` está desusada, use [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) en su lugar). El primer argumento es un nombre de archivo. El segundo argumento es una cadena de C que especifica:  
  
-   Si intenta leer datos del archivo o escribir datos en él.  
  
-   Si desea generar contenido nuevo para el archivo, o crear un archivo si no existía anteriormente, o dejar el contenido existente en su lugar.  
  
-   Si escribe en un archivo puede modificar el contenido existente o solo debe anexar bytes al final del archivo.  
  
-   Si desea manipular una secuencia de texto o una secuencia binaria.  
  
 Una vez que el archivo se abre correctamente, se puede determinar después si la secuencia está orientada a bytes (una secuencia de bytes) o a la anchura (una secuencia ancha). Una secuencia inicialmente es independiente. Al llamar a determinadas funciones para operar en la secuencia, esta se orienta a bytes, mientras que, con otras funciones, esta se orienta a la anchura. Una vez establecida, una secuencia mantiene su orientación hasta que se cierra mediante una llamada a [fclose](../c-runtime-library/reference/fclose-fcloseall.md) o [freopen](../c-runtime-library/reference/freopen-wfreopen.md).  
  
 © 1989-2001 de P.J. Plauger y Jim Brodie. Todos los derechos reservados.  
  
## <a name="see-also"></a>Vea también  
 [Secuencias binarias y de texto](../c-runtime-library/text-and-binary-streams.md)   
 [Secuencias anchas y de bytes](../c-runtime-library/byte-and-wide-streams.md)   
 [Controlar secuencias](../c-runtime-library/controlling-streams.md)   
 [Estados de secuencia](../c-runtime-library/stream-states.md)