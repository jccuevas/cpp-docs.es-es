---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299742"
---
# <a name="dependents"></a>/DEPENDENTS

Vuelca los nombres de los archivos dll de los que importa las funciones de la imagen. Puede usar la lista para determinar qué archivos DLL se redistribuirán con la aplicación o buscar el nombre de una dependencia que falta.

## <a name="syntax"></a>Sintaxis

> **/DEPENDENTS**

Esta opción se aplica a todos los archivos ejecutables especificados en la línea de comandos. No toma ningún argumento.

## <a name="remarks"></a>Comentarios

La opción **/DEPENDENTS** agrega los nombres de los archivos dll desde los que la imagen importa funciones a la salida. Esta opción no vuelca los nombres de las funciones importadas. Para ver los nombres de las funciones importadas, use la opción [/Imports](imports-dumpbin.md) .

En los archivos producidos con la opción del compilador [/GL](gl-whole-program-optimization.md), solo está disponible la opción [/HEADERS DUMPBIN](headers.md).

## <a name="example"></a>Ejemplo

En este ejemplo se muestra el resultado de DUMPBIN de la opción **/DEPENDENTS** en el archivo ejecutable [de cliente integrado Tutorial: Cree y use su propia biblioteca](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)de vínculos dinámicos:

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
