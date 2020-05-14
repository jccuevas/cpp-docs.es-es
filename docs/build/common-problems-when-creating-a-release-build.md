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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328866"
---
# <a name="common-problems-when-creating-a-release-build"></a>Problemas comunes al crear versiones de lanzamiento

Durante el desarrollo, normalmente compilará y probará con una compilación de depuración del proyecto. Si compila la aplicación para una compilación de versión, puede obtener una infracción de acceso.

En la siguiente lista se muestran las diferencias principales entre una compilación de depuración y una compilación de versión (no depuración). Hay otras diferencias, pero a continuación se enumeran las diferencias principales que producirían un error en una aplicación en una compilación de versión, pero no en una compilación de depuración.

- [Diseño del montón](#_core_heap_layout)

- [Compilación](#_core_compilation)

- [Compatibilidad con punteros](#_core_pointer_support)

- [Optimizaciones](#_core_optimizations)

Para obtener información sobre cómo detectar errores de compilación de versión en las compilaciones de depuración, vea el artículo sobre [/GZ (detección de errores de compilación de versión en una compilación de depuración)](reference/gz-enable-stack-frame-run-time-error-checking.md).

## <a name="heap-layout"></a><a name="_core_heap_layout"></a> Diseño del montón

El diseño del montón es el causante del 90 por ciento de los problemas aparentes cuando una aplicación funciona en compilaciones de depuración, pero no de versión.

Al compilar el proyecto para la depuración, se usa el asignador de memoria de depuración. Esto significa que todas las asignaciones de memoria tienen bytes de protección colocados alrededor de ellas. Estos bytes de protección detectan las sobrescrituras de memoria. Dado que el diseño del montón es diferente en las compilaciones de versión y de depuración, una sobrescritura de memoria podría no crear ningún problema en una compilación de depuración, pero puede tener efectos catastróficos en una compilación de versión.

Para obtener más información, vea los artículos [Comprobación de la sobrescritura de la memoria](checking-for-memory-overwrites.md) y [Uso de la compilación de depuración para comprobar si se ha sobrescrito la memoria](using-the-debug-build-to-check-for-memory-overwrite.md).

## <a name="compilation"></a><a name="_core_compilation"></a> Compilación

Muchas de las macros de MFC y gran parte de la implementación de MFC cambian al compilar versiones. En concreto, la macro ASSERT no se evalúa como ningún valor en una compilación de versión, por lo que no se ejecutará ningún código que se encuentre en las instrucciones ASSERT. Para obtener más información, vea el artículo sobre cómo [examinar las instrucciones ASSERT](using-verify-instead-of-assert.md).

Algunas funciones se insertan para aumentar la velocidad de la compilación de versión. Las optimizaciones suelen estar activadas en una compilación de versión. También se usa un asignador de memoria diferente.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a> Compatibilidad con punteros

La falta de información de depuración quita el espaciado interno de la aplicación. En una compilación de versión, los punteros aislados tienen una mayor probabilidad de apuntar a la memoria sin inicializar que a la información de depuración.

## <a name="optimizations"></a><a name="_core_optimizations"></a> Optimizaciones

Dependiendo de la naturaleza de determinados segmentos de código, el compilador de optimización podría generar código inesperado. Esta es la causa menos probable de los problemas de compilación de versión, pero se da a veces. Para obtener una solución, vea [Optimizar el código](optimizing-your-code.md).

## <a name="see-also"></a>Vea también

[Versiones de lanzamiento](release-builds.md)<br/>
[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
