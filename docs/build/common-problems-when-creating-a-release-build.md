---
title: Problemas comunes al crear versiones de lanzamiento
ms.date: 11/04/2016
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
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 9bd1cafe40417872d42f2e9e1427e5f2eccad7a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328866"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problemas comunes al crear versiones de lanzamiento

Durante el desarrollo, normalmente compilará y probará con una compilación de depuración del proyecto. Si, a continuación, compila la aplicación para una compilación de versión, puede obtener una infracción de acceso.

La lista siguiente muestra las diferencias principales entre un debug y una compilación de versión (no depuración). Hay otras diferencias, pero a continuación se muestran las principales diferencias que provocarían un error en una aplicación en una compilación de versión cuando funciona en una compilación de depuración.

- [Diseño del montón](#_core_heap_layout)

- [Compilación](#_core_compilation)

- [Soporte de puntero](#_core_pointer_support)

- [Optimizaciones](#_core_optimizations)

Consulte la opción del compilador [/GZ (Catch Release-Build Errors in Debug Build)](reference/gz-enable-stack-frame-run-time-error-checking.md) para obtener información sobre cómo detectar errores de compilación de versión en compilaciones de depuración.

## <a name="heap-layout"></a><a name="_core_heap_layout"></a>Diseño del montón

El diseño del montón será la causa de aproximadamente el noventa por ciento de los problemas aparentes cuando una aplicación trabaja en la depuración, pero no en la versión.

Al compilar el proyecto para la depuración, está utilizando el asignador de memoria de depuración. Esto significa que todas las asignaciones de memoria tienen bytes de protección colocados alrededor de ellos. Estos bytes de protección detectan una sobrescritura de memoria. Dado que el diseño del montón es diferente entre las versiones de versión y depuración, es posible que una sobrescritura de memoria no cree ningún problema en una compilación de depuración, pero puede tener efectos catastróficos en una compilación de versión.

Para obtener más información, vea [Buscar sobrescritura](checking-for-memory-overwrites.md) de memoria y Usar la compilación de depuración para comprobar la [sobrescritura](using-the-debug-build-to-check-for-memory-overwrite.md)de memoria .

## <a name="compilation"></a><a name="_core_compilation"></a>Compilación

Muchas de las macros MFC y gran parte de la implementación de MFC cambia al compilar para la versión. En particular, la macro ASSERT no se evalúa como nada en una compilación de versión, por lo que no se ejecutará ningún código encontrado en ASSERTs. Para obtener más información, consulte [Examinar instrucciones ASSERT](using-verify-instead-of-assert.md).

Algunas funciones están alineadas para aumentar la velocidad en la versión de lanzamiento. Las optimizaciones generalmente se activan en una versión de lanzamiento. También se está utilizando un asignador de memoria diferente.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a>Soporte de puntero

La falta de información de depuración quita el relleno de la aplicación. En una compilación de versión, los punteros perdidos tienen una mayor probabilidad de apuntar a la memoria no inicializada en lugar de apuntar a la información de depuración.

## <a name="optimizations"></a><a name="_core_optimizations"></a>Optimizaciones

Dependiendo de la naturaleza de ciertos segmentos de código, el compilador de optimización podría generar código inesperado. Esta es la causa menos probable de problemas de compilación de versión, pero surge en ocasiones. Para obtener una solución, consulte [Optimización del código](optimizing-your-code.md).

## <a name="see-also"></a>Consulte también

[Versiones de lanzamiento](release-builds.md)<br/>
[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
