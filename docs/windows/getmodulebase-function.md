---
title: GetModuleBase (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25e4bb6db6114f7d64522dfe145d51ffaabd476a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874212"
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