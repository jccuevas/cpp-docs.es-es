---
title: MixIn (estructura) | Microsoft Docs
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
ms.openlocfilehash: 8fb5fa5288829ef51bf818ad8b7cf3b46edb59bf
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014291"
---
# <a name="mixin-structure"></a>MixIn (estructura)
Garantiza que una clase Runtime deriva de interfaces de Windows Runtime, si las hubiera, y luego de interfaces de COM clásico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
### <a name="parameters"></a>Parámetros  
 *Derivados*  
 Un tipo derivado de la [implementa](../windows/implements-structure.md) estructura.  
  
 *MixInType*  
 Tipo base.  
  
 *hasImplements*  
 **True** si *MixInType* es derivado de la implementación actual del tipo base; **false** en caso contrario.  
  
## <a name="remarks"></a>Comentarios  
 Si una clase se deriva de Windows en tiempo de ejecución y las interfaces de clases COM, la lista de declaración de clase primero debe mostrar ninguna interfaz de Windows en tiempo de ejecución y, a continuación, las interfaces de cualquier COM clásico. **MixIn** garantiza que las interfaces se especifican en el orden correcto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `MixIn`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)