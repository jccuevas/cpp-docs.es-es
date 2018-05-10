---
title: ImplementsHelper (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58f27e418946987633f771bc8d2c3224bc2cd7fd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="implementshelper-structure"></a>ImplementsHelper (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `RuntimeClassFlagsT`  
 Un campo de indicadores que especifica uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) los enumeradores.  
  
 `ILst`  
 Una lista de identificadores de interfaz.  
  
 `IsDelegateToClass`  
 Especifique `true` si la instancia actual de implementa es una clase base del primer identificador de interfaz en `ILst`; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Le ayuda a implementar la [implementa](../windows/implements-structure.md) estructura.  
  
 Esta plantilla recorre una lista de interfaces y los agrega como clases base y como la información necesaria para habilitar QueryInterface.  
  
## <a name="members"></a>Miembros  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ImplementsHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Referencia (biblioteca de tiempo de ejecución de Windows)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)