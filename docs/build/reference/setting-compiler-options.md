---
title: Establecer opciones del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 322d4add32aca1c57b45a601e4704b2ec5d99a02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375811"
---
# <a name="setting-compiler-options"></a>Establecer las opciones del compilador
Las opciones del compilador de C y C++ pueden definirse en el entorno de desarrollo o en la línea de comandos.  
  
## <a name="in-the-development-environment"></a>En el entorno de desarrollo  
 Puede establecer opciones del compilador para cada proyecto en su **páginas de propiedades** cuadro de diálogo. En el panel izquierdo, seleccione **propiedades de configuración**, **C/C++** y, a continuación, elija la categoría de la opción de compilador. En el tema de cada opción del compilador se describe cómo puede definirse y dónde se encuentra en el entorno de desarrollo. Vea [opciones del compilador](../../build/reference/compiler-options.md) para obtener una lista completa.  
  
## <a name="outside-the-development-environment"></a>Fuera del entorno de desarrollo  
 Las opciones del compilador (CL.exe) pueden definirse:  
  
-   [En la línea de comandos](../../build/reference/compiler-command-line-syntax.md)  
  
-   [En archivos de comandos](../../build/reference/cl-command-files.md)  
  
-   [En la variable de entorno de CL](../../build/reference/cl-environment-variables.md)  
  
 Las opciones especificadas en la variable de entorno de CL se usan cada vez que se invoca CL. Si se menciona un archivo de comandos en la variable de entorno de CL o en la línea de comandos, se usarán las opciones especificadas en dicho archivo. A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.  
  
 Las opciones del compilador se procesan "de izquierda a derecha" y, si se detecta un conflicto, tiene prioridad la última opción (la que está situada más a la derecha). La variable de entorno de CL se procesa antes que la línea de comandos, por lo que siempre tendrá prioridad en caso de conflicto con la línea de comandos.  
  
## <a name="additional-compiler-topics"></a>Temas adicionales relacionados con el compilador  
  
-   [Compilación rápida](../../build/reference/fast-compilation.md)  
  
-   [CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)