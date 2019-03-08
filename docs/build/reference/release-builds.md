---
title: Versiones de lanzamiento
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 346beace1979871cfd9bf4ee0d487e7f85a26eaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426100"
---
# <a name="release-builds"></a>Versiones de lanzamiento

Una versión de lanzamiento usa las optimizaciones. Cuando usa las optimizaciones para crear una versión de lanzamiento, el compilador no generará información de depuración simbólica. Llama a la ausencia de información de depuración simbólica, junto con el hecho de que no se genera código para el seguimiento y ASSERT, significa que el tamaño del archivo ejecutable se reduce y, por tanto, será más rápida.

Esta sección contiene información sobre por qué y cuándo se desea cambiar de una compilación de depuración a una versión de lanzamiento. También se tratan algunos de los problemas que puede surgir al cambiar de una depuración a una versión de lanzamiento:

- [Creación de una versión de lanzamiento](../../build/reference/how-to-create-a-release-build.md)

- [Problemas comunes al crear versiones de lanzamiento](../../build/reference/common-problems-when-creating-a-release-build.md)

- [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)

   - [Examinar instrucciones ASSERT](../../build/reference/using-verify-instead-of-assert.md)

   - [Uso de la versión de depuración para comprobar si sobrescrito la memoria](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [Depuración de una versión de lanzamiento](../../build/reference/how-to-debug-a-release-build.md)

   - [Comprobar si se ha sobrescrito la memoria](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>Vea también

[Compilar proyectos de C++ en Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)
