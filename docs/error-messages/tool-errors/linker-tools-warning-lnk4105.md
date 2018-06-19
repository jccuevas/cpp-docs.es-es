---
title: Las herramientas del vinculador LNK4105 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffdd8953e08f38d36bdfc2e68ad6cb8e06fb85b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33304419"
---
# <a name="linker-tools-warning-lnk4105"></a>Advertencia de las herramientas del vinculador LNK4105
ningún argumento especificado con la opción 'opción'; omitiendo la opción  
  
 Esta advertencia sólo aparece cuando la [/libpath](../../build/reference/libpath-additional-libpath.md) opción está establecida. Si no se especifica ningún directorio con esta opción, el vinculador omite la opción y genera este mensaje de advertencia.  
  
 Si no necesita invalidar la configuración de la biblioteca del entorno existente, quite la opción/LIBPATH desde la línea de comandos del vinculador. Si desea usar una ruta de búsqueda alternativa para las bibliotecas, especifique la ruta de acceso alternativa después de la opción/LIBPATH.  
  
## <a name="example"></a>Ejemplo  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 dirigiría al vinculador que busque las bibliotecas requeridas en `c:\filepath\lib` antes de buscar en las ubicaciones predeterminadas.