---
title: "Controlar secuencias | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Controlling Streams"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "controlar secuencias"
  - "secuencias"
  - "secuencias, controlar"
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Controlar secuencias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[fopen](../c-runtime-library/reference/fopen-wfopen.md) devuelve la dirección de un objeto de `FILE`escrito.  Se usa esta dirección como argumento de `stream` a varias funciones de biblioteca para realizar diversas operaciones en un archivo abierto.  Para una secuencia de bytes, toda la entrada tiene lugar como si cada carácter es leído llamando a [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), y salida tiene lugar todo como si cada carácter se escribirá llamando a [fputc](../c-runtime-library/reference/fputc-fputwc.md).  Para una secuencia elevado, toda la entrada tiene lugar como si cada carácter es leído llamando a [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), y salida tiene lugar todo como si cada carácter se escribirá llamando a [fputwc](../c-runtime-library/reference/fputc-fputwc.md).  
  
 Puede cerrar un archivo llamando a [fclose](../c-runtime-library/reference/fclose-fcloseall.md), tras lo cual la dirección del objeto de `FILE` no es válida.  
  
 Un objeto de `FILE` almacena el estado de una secuencia, como:  
  
-   Un valor distinto de cero del indicador de error por una función que encuentra una lectura o de escritura.  
  
-   Un valor distinto de cero del indicador de final de archivo por una función que encuentra el final del archivo mientras lee.  
  
-   Un indicador del archivo \(el archivo posición especifica el byte siguiente en la secuencia para leer o escribir, si el archivo puede admitir la posición de solicitudes.  
  
-   [estado de la secuencia](../c-runtime-library/stream-states.md) especifica si la secuencia aceptará lee o escribe y si la secuencia está sin enlazar, byte orientado a objetos, o orientado a objetos de ancho.  
  
-   Un estado de conversión recuerda el estado de carácter general en parte ensamblado o generado ningún multibyte, así como cualquier estado de cambio para la secuencia de bytes en el archivo\).  
  
-   Un búfer de archivos especifica la dirección y el tamaño de un objeto array que las funciones de biblioteca pueden utilizar para mejorar el rendimiento de las operaciones de lectura y escritura a la secuencia.  
  
 No modifique ningún valor almacenado en un objeto de `FILE` o en un búfer de archivos que especifique para el uso con ese objeto.  No puede copiar un objeto de `FILE` y portably utilizar la dirección de la copia como argumento de `stream` a una función de biblioteca.  
  
## Vea también  
 [Archivos y secuencias](../c-runtime-library/files-and-streams.md)