---
title: Error irrecuperable C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751679"
---
# <a name="fatal-error-c1076"></a>Error irrecuperable C1076

> límite del compilador : se ha alcanzado el límite del montón interno; utilice /Zm para especificar un límite más alto

Este error puede producirse por un exceso de símbolos o de instancias de la plantilla. A partir de Visual Studio 2015, este mensaje puede originarse presión de memoria virtual de Windows causada por muchos de los procesos de compilación paralela. En este caso, la recomendación de usar el **/Zm** se debe omitir la opción a menos que esté usando un `#pragma hdrstop` directiva.

Para resolver este error:

1. Si usa el encabezado precompilado un `#pragma hdrstop` la directiva, use el [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opción para establecer el límite de memoria del compilador en el valor especificado en el [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) mensaje de error. Para obtener más información que incluye cómo establecer este valor en Visual Studio, consulte la sección Comentarios de [/Zm (especificar precompilado encabezado memoria límite de asignación)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Considere la posibilidad de reducir el número de procesos paralelos que se especifican mediante el **/maxcpucount** opción a MSBUILD. EXE junto con el **/MP** opción CL. EXE. Para obtener más información, consulte [problemas de encabezado precompilado (PCH) y las recomendaciones](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Si usa los compiladores hospedados de 32 bits en un sistema operativo de 64 bits, utilice en su lugar los compiladores hospedados de 64 bits. Para obtener más información, vea [Cómo: Habilitar un Toolset de 64 bits Visual C++ en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Elimine los archivos de inclusión innecesarios.

1. Elimine las variables globales que no son necesarias (por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande).

1. Elimine las declaraciones que no utilice.

Si el error C1076 se produce inmediatamente después de que empiece la compilación, el valor especificado para **/Zm** probablemente es demasiado alto para el programa. Reducir el **/Zm** valor.