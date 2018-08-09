---
title: HandleT (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a34b66a6e2c901ddbfb3005a0bdb8fd686317af0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641510"
---
# <a name="handlet-class"></a>HandleT (clase)
Representa un identificador a un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
### <a name="parameters"></a>Parámetros  
 *HandleTraits*  
 Una instancia de la [HandleTraits](../windows/handletraits-structure.md) una estructura que define las características comunes de un controlador.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Traits`|Sinónimo de `HandleTraits`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HandleT::HandleT (constructor)](../windows/handlet-handlet-constructor.md)|Inicializa una nueva instancia de la **HandleT** clase.|  
|[HandleT::~HandleT (destructor)](../windows/handlet-tilde-handlet-destructor.md)|Desinicializa una instancia de la **HandleT** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HandleT::Attach (método)](../windows/handlet-attach-method.md)|Asocia el identificador especificado con el actual **HandleT** objeto.|  
|[HandleT::Close (método)](../windows/handlet-close-method.md)|Cierra el actual **HandleT** objeto.|  
|[HandleT::Detach (método)](../windows/handlet-detach-method.md)|Desasocia actual **HandleT** objeto a partir de su identificador subyacente.|  
|[HandleT::Get (método)](../windows/handlet-get-method.md)|Obtiene el valor del identificador subyacente.|  
|[HandleT::IsValid (método)](../windows/handlet-isvalid-method.md)|Indica si el actual **HandleT** objeto representa un identificador.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HandleT::InternalClose (método)](../windows/handlet-internalclose-method.md)|Cierra el actual **HandleT** objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[HandleT::operator= (operador)](../windows/handlet-operator-assign-operator.md)|Mueve el valor del elemento especificado **HandleT** el objeto actual **HandleT** objeto.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[HandleT::handle_ (miembro de datos)](../windows/handlet-handle-data-member.md)|Contiene el identificador representado por la **HandleT** objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HandleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)