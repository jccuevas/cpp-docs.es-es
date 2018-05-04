---
title: Sintaxis de línea de comandos del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825121a111d47de6b012aad444907363ad8c2a36
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-command-line-syntax"></a>Sintaxis de la línea de comandos del compilador
La línea de comandos de CL se utiliza la sintaxis siguiente:  
  
```  
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]  
```  
  
 En la tabla siguiente describe la entrada para el comando de CL.  
  
|Entrada|Significado|  
|-----------|-------------|  
|*Opción*|Uno o varios [opciones de CL](../../build/reference/compiler-options.md). Tenga en cuenta que todas las opciones se aplican a todos los archivos de origen especificado. Opciones se especifican mediante una barra diagonal (/) o un guión (-). Si una opción toma un argumento, los documentos de descripción de la opción si se permite un espacio entre la opción y los argumentos. Los nombres de opción (excepto para la opción/help) distinguen mayúsculas de minúsculas. Vea [orden de las opciones de CL](../../build/reference/order-of-cl-options.md) para obtener más información.|  
|`file`|El nombre de uno o más archivos de código fuente, archivos .obj o bibliotecas. CL compila archivos de código fuente y pasa los nombres de los archivos .obj y las bibliotecas al vinculador. Vea [sintaxis de nombre de archivo de CL](../../build/reference/cl-filename-syntax.md) para obtener más información.|  
|*Lib*|Uno o más nombres de biblioteca. CL pasa estos nombres al vinculador.|  
|*archivo de comandos*|Un archivo que contiene varias opciones y nombres de archivo. Vea [archivos de comandos de CL](../../build/reference/cl-command-files.md) para obtener más información.|  
|*Elegir vínculo*|Uno o varios [opciones del vinculador](../../build/reference/linker-options.md). CL pasa estas opciones al vinculador.|  
  
 Puede especificar cualquier número de opciones, los nombres de archivo y nombres de biblioteca, siempre y cuando el número de caracteres en la línea de comandos no supera los 1024, límite dictado por el sistema operativo.  
  
 Para obtener información sobre el valor devuelto de cl.exe, vea [valor devuelto de cl.exe](../../build/reference/return-value-of-cl-exe.md) .  
  
> [!NOTE]
>  No se garantiza que el límite de 1024 caracteres de entrada de línea de comandos siguen siendo los mismos en versiones futuras de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)