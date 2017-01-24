---
title: "Secuencias anchas y de bytes | Microsoft Docs"
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
  - "Byte and Wide Streams"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "secuencias de bytes"
  - "secuencias anchas"
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Secuencias anchas y de bytes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una secuencia de bytes trata un archivo como una secuencia de bytes.  En el programa, la secuencia es la secuencia de bytes idéntica.  
  
 Por el contrario, una secuencia de ancho trata un archivo como una secuencia de caracteres generalizados multibyte, que pueden tener una amplia gama de reglas de codificación. \(El texto y los archivos binarios todavía se leen y se escriben como se describió anteriormente.\) En el programa, la secuencia se parece la secuencia correspondiente de caracteres anchos.  Las conversiones entre las dos representaciones aparecen dentro de la biblioteca de c estándar.  Las reglas de conversión se pueden, en principio, modificar por una llamada a [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) que modifique la categoría `LC_CTYPE`.  Cada secuencia de ancho determina las reglas de conversión cuando se orienta de ancho, y conserva estas reglas incluso si los cambios de `LC_CTYPE` category posteriormente.  
  
 La posición dentro de una secuencia de ancho sufre las mismas limitaciones que para los vapores de texto.  Por otra parte, el indicador del archivo \(el archivo posición bien puede tener que tratar con una codificación provincia\- dependiente.  Normalmente, incluye un desplazamiento de bytes en la secuencia y un objeto de `mbstate_t`escrito.  Así, la única manera confiable de obtener un archivo colocar dentro de una secuencia de ancho está llamando [fgetpos](../c-runtime-library/reference/fgetpos.md), y la única manera confiable de restaurar una posición obtuvo esta manera está llamando [fsetpos](../c-runtime-library/reference/fsetpos.md).  
  
## Vea también  
 [Archivos y secuencias](../c-runtime-library/files-and-streams.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)