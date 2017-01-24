---
title: "Secuencias binarias y de texto | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "secuencias binarias"
  - "secuencias de texto"
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Secuencias binarias y de texto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una secuencia de texto consta de una o varias líneas de texto que se pueden escribir en una pantalla centrada en el texto para que pueda leer.  Al leer de una secuencia de texto, el programa lee `NL` \(nueva línea\) al final de cada línea.  Al escribir en una secuencia de texto, el programa escribe `NL` para indicar el final de una línea.  Para hacer coincidir las distintas convenciones entre los entornos de destino para representar el texto en archivos, funciones de biblioteca pueden modificar el número y las representaciones de caracteres transmitidos entre el programa y una secuencia de texto.  
  
 Así, colocándolos en una secuencia de texto está restringido.  Puede obtener el marcador actual del archivo \(el archivo posición llamando a [fgetpos](../c-runtime-library/reference/fgetpos.md) o [ftell](../c-runtime-library/reference/ftell-ftelli64.md).  Puede colocar una secuencia de texto en una posición obtuvo de esta manera, o al principio o el final de la secuencia, llamando a [fsetpos](../c-runtime-library/reference/fsetpos.md) o [fseek](../c-runtime-library/reference/fseek-fseeki64.md).  Cualquier otro cambio de posición puede no admitir bien.  
  
 Para la portabilidad máxima, el programa no debe escribir:  
  
-   Archivos vacíos.  
  
-   Caracteres de espacio al final de una línea.  
  
-   Líneas parciales \(omitiendo `NL` al final de un archivo\).  
  
-   caracteres distintos de los caracteres imprimibles, de NL, y de `HT` \(tabulación horizontal\).  
  
 Si sigue estas reglas, la secuencia de caracteres que se lee de una secuencia de texto \(como caracteres de byte o multibyte\) coincidirá con la secuencia de caracteres que escribió en la secuencia de texto cuando se creó el archivo.  Si no, funciones de biblioteca pueden quitar un archivo que se crea si el archivo está vacío cuando se cierra.  O pueden modificar o eliminar los caracteres que escribe en el archivo.  
  
 Una secuencia binaria consta de uno o más bytes de información arbitraria.  Puede escribir el valor almacenado en un objeto arbitrario a la secuencia binaria y la lectura de \(byte\- orientada\) exactamente lo que se almacenó en el objeto escribió.  Las funciones de biblioteca no modifican los bytes que se transmite entre el programa y una secuencia binaria.  Pueden, sin embargo, se anexa un número arbitrario de bytes nulos al archivo que escribe en una secuencia binaria.  El programa debe resolver estos bytes nulos adicionales al final de una secuencia binaria.  
  
 Así, la posición dentro de una secuencia binaria es bien definido, a excepción de la posición relativa al final de la secuencia.  Puede obtener y modificar el marcador actual del archivo \(el archivo posición igual que para una secuencia de texto.  Por otra parte, los desplazamientos utilizados por [ftell](../c-runtime-library/reference/ftell-ftelli64.md) y [fseek](../c-runtime-library/reference/fseek-fseeki64.md) cuentan bytes desde el principio de la secuencia \(el byte cero\), lo que la aritmética de enteros en estas diferencias produce resultados predecibles.  
  
 Una secuencia de bytes trata un archivo como una secuencia de bytes.  En el programa, la secuencia es la misma secuencia de bytes, a excepción de las modificaciones posibles descritas anteriormente.  
  
## Vea también  
 [Archivos y secuencias](../c-runtime-library/files-and-streams.md)