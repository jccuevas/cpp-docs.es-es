---
title: Compilaciones de versiones de C++ (Visual Studio)
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 46ae5e0f3d545f0e3e004f612314ab416b270fd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168829"
---
# <a name="release-builds"></a>Versiones de lanzamiento

Las compilaciones de versiones usan optimizaciones. Si usa optimizaciones para crear una compilación de versión, el compilador no generará información de depuración simbólica. La ausencia de información de depuración simbólica, junto con el hecho de que el código no se genera para las llamadas de seguimiento y ASSERT, significa que se reduce el tamaño del archivo ejecutable y, por tanto, será más rápido.

## <a name="in-this-section"></a>En esta sección

[Problemas comunes al crear versiones de lanzamiento](common-problems-when-creating-a-release-build.md)<br/>
[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)<br/>
[Usar VERIFY en lugar de ASSERT](using-verify-instead-of-assert.md)<br/>
[Usar la versión de depuración para comprobar si se ha sobrescrito la memoria](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Cómo: Depuración de una compilación de versión](how-to-debug-a-release-build.md)<br/>
[Comprobar si se ha sobrescrito la memoria](checking-for-memory-overwrites.md)<br/>
[Optimizar el código](optimizing-your-code.md)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)
