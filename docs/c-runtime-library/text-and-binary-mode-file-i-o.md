---
title: "E/S de archivo en modo texto y en modo binario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acceso binario"
  - "acceso binario, E/S de archivo en modo binario"
  - "archivos [C++], funciones de apertura"
  - "funciones [CRT], acceso a archivos"
  - "E/S [CRT], binaria"
  - "E/S [CRT], archivos de texto"
  - "E/S [CRT], modos de traducción"
  - "archivos de texto, E/S"
  - "modos de traducción (E/S de archivo)"
  - "traslación, modos"
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# E/S de archivo en modo texto y en modo binario
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operaciones de E\/S de archivos tienen lugar en uno de los dos modos de traducción, texto o binario, dependiendo del modo en que se abrirá el archivo.  Los archivos de datos se procesan normalmente en modo de texto.  Para controlar el archivo de modalidad de traducción, se puede:  
  
-   Mantenga la configuración predeterminada actual y especificar el modo alternativo sólo cuando se abren los archivos seleccionados.  
  
-   Utilice la función [\_set\_fmode](../c-runtime-library/reference/set-fmode.md) para cambiar al modo predeterminado de nuevo los archivos abiertos.  Utilice [\_get\_fmode](../c-runtime-library/reference/get-fmode.md) para buscar el modo predeterminado actual.  La configuración predeterminada inicial es el modo de texto \(`_O_TEXT`\).  
  
-   Cambie el de modalidad de traducción predeterminado estableciendo directamente la variable global [\_fmode](../c-runtime-library/fmode.md) en el programa.  La función `_set_fmode` establece el valor de esta variable, pero también puede establecerse directamente.  
  
 Cuando se llama a una función de archivo \(el archivo Abrir como [\_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [\_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) o [\_sopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md), puede reemplazar el valor predeterminado actual de `_fmode` especificando el argumento adecuado a la función [\_set\_fmode](../c-runtime-library/reference/set-fmode.md).  `stdin`, `stdout`, y secuencias de `stderr` abra siempre en modo de texto de forma predeterminada; también puede invalidar este valor predeterminado al abrir cualquiera de estos archivos.  El uso [\_setmode](../c-runtime-library/reference/setmode.md) de cambiar el de modalidad de traducción mediante descriptor de archivo después de archivo está abierto.  
  
## Vea también  
 [Entrada y salida](../c-runtime-library/input-and-output.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)