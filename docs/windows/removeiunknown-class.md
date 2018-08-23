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
ms.openlocfilehash: 11751bf4e6f43e18fddb71a5ba2fd331a6d36977
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599376"
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