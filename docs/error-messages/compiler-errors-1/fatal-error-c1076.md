---
title: Error irrecuperable C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204183"
---
# <a name="fatal-error-c1076"></a>Error irrecuperable C1076

> límite del compilador : se ha alcanzado el límite del montón interno; utilice /Zm para especificar un límite más alto

Este error puede producirse por un exceso de símbolos o de instancias de la plantilla. A partir de Visual Studio 2015, este mensaje puede deberse a la presión de memoria virtual de Windows causada por demasiados procesos de compilación en paralelo. En este caso, se debe pasar por alto la recomendación de utilizar la opción **/ZM** , a menos que se use una directiva de `#pragma hdrstop`.

Para solucionar este error:

1. Si el encabezado precompilado usa una directiva de `#pragma hdrstop`, use la opción [/ZM](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) para establecer el límite de memoria del compilador en el valor especificado en el mensaje de error [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) . Para obtener más información sobre cómo establecer este valor en Visual Studio, vea la sección Comentarios en [/ZM (especificar el límite de asignación de memoria del encabezado precompilado)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Considere la posibilidad de reducir el número de procesos paralelos especificados mediante la opción **/maxcpucount** a MSBuild. EXE junto con la opción **/MP** en cl. Ejecutable. Para obtener más información, vea [problemas y recomendaciones del encabezado precompilado (PCH)](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Si usa los compiladores hospedados de 32 bits en un sistema operativo de 64 bits, utilice en su lugar los compiladores hospedados de 64 bits. Para obtener más información, vea [Cómo: habilitar un conjunto de herramientas visual C++ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Elimine los archivos de inclusión innecesarios.

1. Elimine las variables globales que no son necesarias (por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande).

1. Elimine las declaraciones que no utilice.

Si C1076 se produce inmediatamente después de que se inicie la compilación, es probable que el valor especificado para **/ZM** sea demasiado alto para el programa. Reduzca el valor de **/ZM** .
