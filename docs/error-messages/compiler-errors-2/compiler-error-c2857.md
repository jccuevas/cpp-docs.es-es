---
title: Error del compilador C2857 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49e94e12b4cdf07d9f7fe74dd481bbc032a937eb
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601384"
---
# <a name="compiler-error-c2857"></a>Error del compilador C2857

> ' #include ' instrucción especificada con la/Yc*filename* no se encontró la opción de línea de comandos en el archivo de origen

El [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción especifica el nombre de un archivo de inclusión que no se incluye en el archivo de origen que se está compilando.

## <a name="remarks"></a>Comentarios

Cuando se usa el **/Yc**<em>filename</em> opción en un archivo de origen para crear un archivo de encabezado precompilado (PCH), que el archivo de origen debe incluir el *filename* archivo de encabezado. Cada archivo que incluya el archivo de código fuente, hasta e incluyendo especificado *filename*, se incluye en el archivo PCH. En otros archivos de código fuente compilados mediante la **/Yu**<em>filename</em> opción para usar el PCH de archivos, un archivo de inclusión de *filename* debe ser la primera línea de sin comentarios en el archivo. El compilador omite todo lo que antes de que se incluyen en el archivo de origen.

Este error puede deberse a un `#include "filename"` instrucción en un bloque de compilación condicional que no se compila en el archivo de origen PCH.

## <a name="example"></a>Ejemplo

En un uso típico, un archivo de código fuente en el proyecto se designa como el archivo de código fuente PCH y un archivo de encabezado se utiliza como el archivo de encabezado PCH. Un archivo de encabezado PCH típico tiene todos los encabezados de la biblioteca usados en el proyecto, pero los encabezados no locales que aún están en desarrollo. En este ejemplo, el archivo de encabezado PCH denominado *my_pch.h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

El archivo de código fuente PCH compilado mediante la **/Yc**<em>my_pch.h</em> opción. Si el compilador no encuentra un archivo de inclusión de este archivo de encabezado PCH, genera C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Para usar este archivo PCH, archivos de código fuente deben compilarse con la **/Yu**<em>my_pch.h</em> opción. El archivo de encabezado PCH debe incluirse en primer lugar en los archivos de origen que utilizan el PCH:

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```