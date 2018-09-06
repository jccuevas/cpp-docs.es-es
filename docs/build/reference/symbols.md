---
title: -SYMBOLS | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /symbols
dev_langs:
- C++
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4f0787ca6bcf57f9d336da94b1f47593f05793b
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894582"
---
# <a name="symbols"></a>/SYMBOLS

```  
/SYMBOLS
```  

Esta opción muestra la tabla de símbolos COFF. Tablas de símbolos existen en todos los archivos de objeto. Una tabla de símbolos COFF aparece en un archivo de imagen solo si está vinculada con/Debug.

La siguiente es una descripción de la salida de /SYMBOLS. Encontrará información adicional sobre el significado de salida /SYMBOLS en winnt.h (IMAGE_SYMBOL e IMAGE_AUX_SYMBOL) o la documentación de COFF.

Dado el volcado de memoria siguientes:

```  
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```  

## <a name="remarks"></a>Comentarios

La siguiente descripción, para las líneas que comienzan con un número de símbolos, describe las columnas que contienen información relevante para los usuarios:

- El primer número de tres dígitos es el índice/número de símbolos.

- Si la tercera columna contiene SECT*x*, el símbolo está definido en esa sección del archivo objeto. Pero, si aparece UNDEF no está definido en ese objeto y se deben resolver en otro lugar.

- La quinta columna (Static, External) indica si el símbolo es visible solo dentro de ese objeto, o si es público (visible externamente). Un símbolo estático, _sym, no se puede vincular a un _sym símbolos públicos. serían dos instancias distintas de funciones denominadas _sym.

La última columna de una línea numerada es el nombre del símbolo, representativo y no representativos.

Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)