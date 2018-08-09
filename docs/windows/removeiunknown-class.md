---
title: RemoveIUnknown (clase) | Microsoft Docs
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
ms.openlocfilehash: dd52dcdc5fed543d65311aaa7e8a61a9d2019b8a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020296"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown (Clase)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Una clase.  
  
## <a name="remarks"></a>Comentarios  
 Convierte un tipo que es equivalente a un `IUnknown`-tipo de función, pero tiene no virtuales `QueryInterface`, `AddRef`, y `Release` funciones miembro.  
  
 De forma predeterminada, los métodos COM proporcionan virtual `QueryInterface`, `AddRef`, y `Release` métodos. Sin embargo, `ComPtr` no requieren la sobrecarga de métodos virtuales. `RemoveIUnknown` elimina esa sobrecarga proporcionando privado y no virtuales `QueryInterface`, `AddRef`, y `Release` métodos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`ReturnType`|Un sinónimo para un tipo que es equivalente al parámetro de plantilla *T* pero tiene no virtuales `IUnknown` miembros.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `T`  
  
 `RemoveIUnknown`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)