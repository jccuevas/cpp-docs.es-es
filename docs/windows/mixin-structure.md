---
title: MixIn (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
dev_langs:
- C++
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b20dac5f189a51a1610da45e43e03e51ff1c3610
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876168"
---
# <a name="mixin-structure"></a>MixIn (estructura)
Garantiza que una clase Runtime deriva de interfaces de Windows Runtime, si las hubiera, y luego de interfaces de COM clásico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Derived`  
 Un tipo derivado de la [implementa](../windows/implements-structure.md) estructura.  
  
 `MixInType`  
 Tipo base.  
  
 `hasImplements`  
 `true` Si `MixInType` es derivado de la implementación actual del tipo base; `false` en caso contrario.  
  
## <a name="remarks"></a>Comentarios  
 Si una clase se deriva de Windows en tiempo de ejecución y las interfaces de clase COM, la lista de declaración de clase en primer lugar debe mostrar ninguna interfaz en tiempo de ejecución de Windows y, a continuación, cualquier COM clásico interfaces. MixIn garantiza que las interfaces se especifican en el orden correcto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `MixIn`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)