---
title: "GetModuleBase (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19f575705b1f8680a68e9100f20be66ca22ec87a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="getmodulebase-function"></a>GetModuleBase (Función)
Recupera un [ModuleBase](../windows/modulebase-class.md) puntero que permite aumentar y disminuir el recuento de referencias de un [RuntimeClass](../windows/runtimeclass-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un puntero a un `ModuleBase` objeto.  
  
## <a name="remarks"></a>Comentarios  
 Esta función se usa internamente para aumentar y disminuir recuentos de referencias de objeto.  
  
 Puede usar esta función para controlar los recuentos de referencia mediante una llamada a [modulebase:: Incrementobjectcount](../windows/modulebase-incrementobjectcount-method.md) y [modulebase:: Decrementobjectcount](../windows/modulebase-decrementobjectcount-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)