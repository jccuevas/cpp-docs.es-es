---
title: "Estados de secuencia | Microsoft Docs"
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
  - "secuencias, estados"
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Estados de secuencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muestra los estados válidos, las transiciones de estado, para una secuencia en la ilustración siguiente.  
  
 ![Secuencia](../c-runtime-library/media/stream.png "stream")  
  
 Cada uno de los círculos denota un estado estable.  Cada una de las líneas indica una transición que puede producirse como resultado de una llamada de función que opera en la secuencia.  Cinco grupos de funciones pueden producir las transiciones de estado.  
  
 Las funciones de los tres primeros grupos se declaran en \<stdio.h:\>  
  
-   La lectura de bytes funciona — [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fread](../c-runtime-library/reference/fread.md), [fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc](../c-runtime-library/reference/getc-getwc.md), [getchar](../c-runtime-library/reference/getc-getwc.md), [obtiene](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), y [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)  
  
-   La escritura de bytes funciona — [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc](../c-runtime-library/reference/fputc-fputwc.md), [fputs](../c-runtime-library/reference/fputs-fputws.md), [fwrite](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc](../c-runtime-library/reference/putc-putwc.md), [putchar](../c-runtime-library/reference/putc-putwc.md), [coloca](../c-runtime-library/reference/puts-putws.md), [vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), y [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
  
-   La posición funciona — [fflush](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos](../c-runtime-library/reference/fsetpos.md), y [rebobinado](../c-runtime-library/reference/rewind.md)  
  
 Restantes las funciones de los dos grupos se declaran en \<wchar.h:\>  
  
-   De ancho las funciones read — [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc](../c-runtime-library/reference/getc-getwc.md), [getwchar](../c-runtime-library/reference/getc-getwc.md), [ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md), y [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),  
  
-   Las funciones amplias de escritura — [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc](../c-runtime-library/reference/fputc-fputwc.md), [fputws](../c-runtime-library/reference/fputs-fputws.md), [putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), y [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),  
  
 El diagrama de estados muestra que debe llamar a una de las funciones de la posición entre la escritura y operaciones de lectura:  
  
-   No puede llamar a una función de lectura si la última operación en la secuencia era una escritura.  
  
-   No puede llamar a una función de escritura si la última operación en la secuencia era una lectura, a menos que esa operación de lectura establezca la marca de fin de archivo.  
  
 Finalmente, el diagrama de estado se muestra una operación de posición nunca reduce el número de llamadas de función válidas que pueden seguir.  
  
## Vea también  
 [Archivos y secuencias](../c-runtime-library/files-and-streams.md)