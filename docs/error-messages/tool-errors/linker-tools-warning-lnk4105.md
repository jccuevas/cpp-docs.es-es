---
title: Las herramientas del vinculador LNK4105 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4105
dev_langs: C++
helpviewer_keywords: LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d64ff3756f709820c7e25b2986b8529a364139e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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