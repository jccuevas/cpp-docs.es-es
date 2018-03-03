---
title: Versiones de lanzamiento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12e81b26cd83214a5d62a42689bfc3a866ef1c10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="release-builds"></a>Versiones de lanzamiento
Una versión de lanzamiento utiliza optimizaciones. Cuando se utilizan optimizaciones para crear una versión de lanzamiento, el compilador no generará información de depuración simbólica. Llama a la ausencia de información de depuración simbólica, junto con el hecho de que no se genera código para el seguimiento y ASSERT, significa que el tamaño del archivo ejecutable se reduce y, por tanto, será más rápida.  
  
 En esta sección se muestra información sobre la razón y el momento necesite cambiar desde una versión de depuración a una versión de lanzamiento. También se describen algunos de los problemas que pueden producirse al cambiar de una depuración a una versión de lanzamiento:  
  
-   [Crear una versión de lanzamiento](../../build/reference/how-to-create-a-release-build.md)  
  
-   [Problemas comunes al crear versiones de lanzamiento](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)  
  
    -   [Examinar instrucciones ASSERT](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [Uso de la versión de depuración para comprobar si se ha sobrescrito de memoria](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [Depurar una versión de lanzamiento](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [Comprobar si se ha sobrescrito la memoria](../../build/reference/checking-for-memory-overwrites.md)  
  
## <a name="see-also"></a>Vea también  
 [Compilar proyectos de C++ en Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)   
 [Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)