---
title: Problemas comunes al crear una versión de lanzamiento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b423f173bfa2d7fdc3fd8e97fe9eb42cf8e76f3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702460"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problemas comunes al crear versiones de lanzamiento

Durante el desarrollo, normalmente se genere y pruebe con una compilación de depuración del proyecto. Si, a continuación, compila la aplicación para una versión de lanzamiento, obtendrá una infracción de acceso.

La siguiente lista muestra las diferencias principales entre una depuración y lanzamiento (nondebug). Hay otras diferencias, pero las siguientes son las principales diferencias que provocaría un error en una aplicación en una versión de lanzamiento cuando funciona en una compilación de depuración.

- [Disposición del montón](#_core_heap_layout)

- [Compilación](#_core_compilation)

- [Soporte técnico de puntero](#_core_pointer_support)

- [optimizaciones](#_core_optimizations)

Consulte la [/GZ (detectar errores de compilación de versión de depuración)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) opción del compilador para obtener información sobre cómo detectar versión generar errores en las compilaciones de depuración.

##  <a name="_core_heap_layout"></a> Disposición del montón

Disposición del montón es la causa del noventa por ciento de los problemas cuando una aplicación funciona en depuración, pero no la versión.

Al compilar el proyecto para la depuración, está usando el asignador de memoria de depuración. Esto significa que todas las asignaciones de memoria tienen bytes de protección en torno a ellas. Estos bytes de protección detectan una sobrescritura de memoria. Dado que el diseño de montón es diferente entre el lanzamiento y depuración versiones, una sobrescritura de memoria no se puede crear cualquier problema en una compilación de depuración, pero podría tener efectos catastróficos en una versión de lanzamiento.

Para obtener más información, consulte [comprobar la sobrescritura de memoria](../../build/reference/checking-for-memory-overwrites.md) y [usar la versión de depuración para comprobar para la sobrescritura de memoria](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md).

##  <a name="_core_compilation"></a> Compilación

Muchas de las macros MFC y gran parte de los cambios de implementación de MFC cuando generan versiones de lanzamiento. En concreto, la macro ASSERT no se evalúa en una versión de lanzamiento, por lo que se ejecutará ningún código incluido en instrucciones Assert. Para obtener más información, consulte [Examinar instrucciones ASSERT](../../build/reference/using-verify-instead-of-assert.md).

Algunas funciones se alinean para incrementar la velocidad en la versión de lanzamiento. Por lo general, las optimizaciones están activadas en una versión de lanzamiento. También se utiliza un asignador de memoria diferente.

##  <a name="_core_pointer_support"></a> Soporte técnico de puntero

La falta de información de depuración, quita el relleno de la aplicación. En una versión de lanzamiento, los punteros perdidos tienen una mayor probabilidad de que apunta a la memoria sin inicializar en lugar de apuntar a la información de depuración.

##  <a name="_core_optimizations"></a> optimizaciones

Según la naturaleza de ciertos segmentos de código, el compilador de optimización podría generar código inesperado. Esta es la causa menos probable de problemas de compilación de versión, pero surgen en alguna ocasión. Para una solución, vea [optimizar el código](../../build/reference/optimizing-your-code.md).

## <a name="see-also"></a>Vea también

[Versiones de lanzamiento](../../build/reference/release-builds.md)<br/>
[Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)