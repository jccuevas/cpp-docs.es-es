---
title: IsBaseOfStrict (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
dev_langs:
- C++
helpviewer_keywords:
- IsBaseOfStrict structure
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4690c15adac7be66ca916b1fc0f769e6c50190c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017908"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (estructura)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
### <a name="parameters"></a>Parámetros  
 *base*  
 El tipo base.  
  
 *Derivados*  
 El tipo derivado.  
  
## <a name="remarks"></a>Comentarios  
 Comprueba si un tipo es la base de otro.  
  
 La primera plantilla comprueba si un tipo se deriva de un tipo base, que podría producir **true** o **false**. La segunda plantilla comprueba si un tipo se deriva de sí misma, que siempre produce **false**.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[IsBaseOfStrict::value (constante)](../windows/isbaseofstrict-value-constant.md)|Indica si un tipo es la base de otro.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IsBaseOfStrict`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)