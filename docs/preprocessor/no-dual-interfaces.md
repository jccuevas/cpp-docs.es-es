---
title: no_dual_interfaces | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8923adb4cf2e92d72bf656064c6de8fc66e2a91
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Específicos de C++**  
  
 Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el contenedor llamará al método a través de la tabla de funciones virtuales para la interfaz. Con `no_dual_interfaces`, el contenedor llama en su lugar **IDispatch:: Invoke** para invocar el método.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)