---
title: VERSIÓN (C/C ++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63ea65a8e3732ee17cc30b3382aa7ebc56e48f59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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