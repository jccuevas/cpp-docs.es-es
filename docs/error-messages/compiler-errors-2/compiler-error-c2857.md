---
title: Error del compilador C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201856"
---
# <a name="compiler-error-c2857"></a>Error del compilador C2857

> no se encontró la instrucción ' #include ' especificada con la opción de línea de comandos/YC*filename* en el archivo de código fuente

La opción [/YC](../../build/reference/yc-create-precompiled-header-file.md) especifica el nombre de un archivo de inclusión que no está incluido en el archivo de código fuente que se está compilando.

## <a name="remarks"></a>Observaciones

Cuando se usa la opción **/YC**<em>filename</em> en un archivo de código fuente para crear un archivo de encabezado precompilado (PCH), ese archivo de origen debe incluir el archivo de encabezado del *nombre* de archivo. Todos los archivos incluidos en el archivo de código fuente, hasta el *nombre*de archivo especificado, inclusive, se incluyen en el archivo PCH. En otros archivos de código fuente compilados con la opción **/Yu**<em>filename</em> para usar el archivo PCH, una inclusión de *filename* debe ser la primera línea que no sea de comentario en el archivo. El compilador omite todo lo que haya en el archivo de código fuente antes de este include.

Este error puede deberse a una instrucción `#include "filename"` en un bloque de compilación condicional que no está compilado en el archivo de código fuente PCH.

## <a name="example"></a>Ejemplo

En el uso típico, un archivo de código fuente del proyecto se designa como el archivo de código fuente PCH y un archivo de encabezado se utiliza como archivo de encabezado PCH. Un archivo de encabezado PCH típico tiene todos los encabezados de biblioteca que se usan en el proyecto, pero no los encabezados locales que todavía están en desarrollo. En este ejemplo, el archivo de encabezado PCH se denomina *my_pch. h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

El archivo de código fuente PCH se compila mediante la opción **/yc**<em>my_pch. h</em> . Si el compilador no encuentra una inclusión de este archivo de encabezado PCH, genera C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Para usar este archivo PCH, los archivos de código fuente deben compilarse con la opción **/yu**<em>my_pch. h</em> . El archivo de encabezado PCH debe incluirse primero en los archivos de código fuente que usan el PCH:

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
