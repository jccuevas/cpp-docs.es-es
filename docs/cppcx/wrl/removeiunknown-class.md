---
title: RemoveIUnknown (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: bfe397f64650caedab1408f1f74fabd005dd98cf
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785784"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
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

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)