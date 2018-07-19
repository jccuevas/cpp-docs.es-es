---
title: RemoveIUnknown (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb005bc3cbf411a7d5b5ddbfa44cd6aecf802105
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879547"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown (Clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase.  
  
## <a name="remarks"></a>Comentarios  
 Crea un tipo que es equivalente a un `IUnknown`-basado en tipo, pero tiene no virtuales `QueryInterface`, `AddRef`, y `Release` funciones miembro.  
  
 De manera predeterminada, los métodos COM proporcionan virtual `QueryInterface`, `AddRef`y métodos de la versión. Sin embargo, `ComPtr` no requiere la sobrecarga de métodos virtuales. `RemoveIUnknown` elimina la carga de ejecución proporcionando privado y no virtual `QueryInterface`, `AddRef`, y `Release` métodos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`ReturnType`|Un sinónimo para un tipo que es equivalente al parámetro de plantilla `T` pero tiene miembros de IUnknown no virtuales.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)