---
title: ImplementsHelper (estructura) | Microsoft Docs
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
ms.openlocfilehash: 5e5da95e6cfb276704b5cd6150e4abc2921a5701
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605622"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (estructura)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
### <a name="parameters"></a>Parámetros  
 *RuntimeClassFlagsT*  
 Un campo de marcas que especifica uno o más [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) enumeradores.  
  
 *ILst*  
 Una lista de identificadores de interfaz.  
  
 *IsDelegateToClass*  
 Especificar **true** si la instancia actual de `Implements` es una clase base de la primera Id. de interfaz en *ILst*; en caso contrario, **false**.  
  
## <a name="remarks"></a>Comentarios  
 Ayuda a implementar la [implementa](../windows/implements-structure.md) estructura.  
  
 Esta plantilla atraviesa una lista de interfaces y los agrega como clases base y como la información necesaria para habilitar QueryInterface.  
  
## <a name="members"></a>Miembros  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ImplementsHelper`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Referencia (biblioteca de tiempo de ejecución de Windows)](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)