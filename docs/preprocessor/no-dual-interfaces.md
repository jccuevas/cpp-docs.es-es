---
title: no_dual_interfaces | Microsoft Docs
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
ms.openlocfilehash: f1e919e48b79c9fe98a7a33257ebd0f70061d788
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539475"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Específicos de C++**  
  
Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Comentarios  
 
Normalmente, el contenedor llamará al método a través de la tabla de funciones virtuales para la interfaz. Con **no_dual_interfaces**, el contenedor en su lugar llama `IDispatch::Invoke` para invocar el método.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)