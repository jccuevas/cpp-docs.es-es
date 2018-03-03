---
title: RemoveIUnknown (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b62362004f0528b16ef3dac7cbe601b8b85ce3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 De manera predeterminada, los métodos COM proporcionan virtual `QueryInterface`, `AddRef`y métodos de la versión. Sin embargo, `ComPtr` no requiere la sobrecarga de métodos virtuales. `RemoveIUnknown`elimina la carga de ejecución proporcionando privado y no virtual `QueryInterface`, `AddRef`, y `Release` métodos.  
  
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