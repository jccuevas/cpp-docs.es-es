---
title: VERSIÓN (C/C ++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcaf4e113af6182a2d3d735e4c668b62336e2c79
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="version-cc"></a>VERSION (C/C++)
Indica a LINK que ponga un número en el encabezado del archivo .exe o DLL.  
  
```  
VERSION major[.minor]  
```  
  
## <a name="remarks"></a>Comentarios  
 El *principal* y *secundaria* argumentos son números decimales comprendidos en el intervalo comprendido entre 0 y 65.535. El valor predeterminado es la versión 0.0.  
  
 Un modo equivalente a especificar un número de versión es con la [información de versión](../../build/reference/version-version-information.md) (/ versión) opción.  
  
## <a name="see-also"></a>Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)