---
title: "/SYMBOLS | Microsoft Docs"
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
  - "/symbols"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SYMBOLS (opción de dumpbin)"
  - "símbolos públicos"
  - "tabla de símbolos"
  - "SYMBOLS (opción de dumpbin)"
  - "-SYMBOLS (opción de dumpbin)"
  - "símbolos, mostrar tabla de símbolos COFF"
  - "símbolos, volcar"
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SYMBOLS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SYMBOLS  
```  
  
 Esta opción muestra la tabla de símbolos COFF.  En todos los archivos objeto existen tablas de símbolos.  En un archivo de imagen sólo aparecerá una tabla de símbolos COFF si se vincula a la opción \/DEBUG.  
  
 A continuación se muestra una descripción del resultado de la opción \/SYMBOLS.  Encontrará más información acerca del significado del resultado de \/SYMBOLS en winnt.h \(IMAGE\_SYMBOL e IMAGE\_AUX\_SYMBOL\) o en la documentación de COFF.  
  
 Veamos el siguiente volcado de memoria de ejemplo:  
  
```  
Dump of file main.obj  
File Type: COFF OBJECT  
  
COFF    SYMBOL    TABLE  
000    00000000   DEBUG      notype      Filename      | .file  
      main.cpp  
002   000B1FDB   ABS      notype      Static      | @comp.id  
003   00000000   SECT1      notype      Static      | .drectve  
      Section length       26, #relocs   0, #linenums    0, checksum 722C964F  
005   00000000   SECT2      notype      Static      | .text  
      Section length      23, #relocs      1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007   00000000   SECT2      notype ()   External      | _main  
008   00000000   UNDEF      notype ()   External      | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  
  
String Table Size = 0x10 bytes  
  
Summary  
  
      26 .drectve  
      23 .text  
```  
  
## Comentarios  
 En la siguiente descripción, en las líneas que empiezan por un número de símbolo, se describen columnas que contienen información relevante para los usuarios:  
  
-   El primer número de tres dígitos es el índice o número de símbolo.  
  
-   Si la tercera columna contiene SECT*x*, indica que el símbolo está definido en esa sección del archivo objeto.  No obstante, si aparece UNDEF, el símbolo no está definido en ese objeto y debe resolverse en otra parte.  
  
-   La quinta columna \(Static, External\) indica si el símbolo sólo está visible dentro de ese objeto o si es público \(visible externamente\).  No se puede vincular un símbolo de tipo Static denominado \_sym a un símbolo Public también denominado \_sym, ya que habría dos instancias diferentes de funciones con el mismo nombre, \_sym.  
  
 La última columna de una línea numerada es el nombre del símbolo \(en formato representativo y en formato no representativo\).  
  
 En los archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md) sólo está disponible la opción [\/HEADERS](../../build/reference/headers.md) de DUMPBIN.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)