---
title: RemoveIUnknown (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213621"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown (Clase)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Clase.

## <a name="remarks"></a>Observaciones

Crea un tipo que es equivalente a un tipo basado en `IUnknown`, pero tiene funciones miembro `QueryInterface`, `AddRef`y `Release` no virtuales.

De forma predeterminada, los métodos COM proporcionan métodos virtuales `QueryInterface`, `AddRef`y `Release`. Sin embargo, `ComPtr` no requiere la sobrecarga de los métodos virtuales. `RemoveIUnknown` elimina esa sobrecarga proporcionando métodos de `QueryInterface`, `AddRef`y `Release` privados y no virtuales.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`ReturnType`|Sinónimo de un tipo que es equivalente al parámetro de plantilla *T* , pero que tiene miembros `IUnknown` no virtuales.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`RemoveIUnknown`

## <a name="requirements"></a>Requisitos

**Encabezado:** client.h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
