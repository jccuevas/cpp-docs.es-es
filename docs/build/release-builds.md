---
title: Compilaciones de versión de C++ - Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 6167c024ae76952573475a815f24d2cf4be01119
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828035"
---
# <a name="release-builds"></a>Versiones de lanzamiento

Una versión de lanzamiento usa las optimizaciones. Cuando usa las optimizaciones para crear una versión de lanzamiento, el compilador no generará información de depuración simbólica. Llama a la ausencia de información de depuración simbólica, junto con el hecho de que no se genera código para el seguimiento y ASSERT, significa que el tamaño del archivo ejecutable se reduce y, por tanto, será más rápida.

## <a name="in-this-section"></a>En esta sección

[Problemas comunes al crear versiones de lanzamiento](common-problems-when-creating-a-release-build.md)<br/>
[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)<br/>
[Usar VERIFY en lugar de ASSERT](using-verify-instead-of-assert.md)<br/>
[Usar la versión de depuración para comprobar si se ha sobrescrito la memoria](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Cómo: Depuración de una compilación de versión](how-to-debug-a-release-build.md)<br/>
[Comprobar si se ha sobrescrito la memoria](checking-for-memory-overwrites.md)<br/>
[Optimizar el código](optimizing-your-code.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)