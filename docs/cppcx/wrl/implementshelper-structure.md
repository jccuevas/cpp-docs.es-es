---
title: ImplementsHelper (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: 250a59152e9b41eb48c453caaa696fdc8ca3d3b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786054"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parámetros

*RuntimeClassFlagsT*<br/>
Un campo de marcas que especifica uno o más [RuntimeClassType](runtimeclasstype-enumeration.md) enumeradores.

*ILst*<br/>
Una lista de identificadores de interfaz.

*IsDelegateToClass*<br/>
Especificar **true** si la instancia actual de `Implements` es una clase base de la primera Id. de interfaz en *ILst*; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Ayuda a implementar la [implementa](implements-structure.md) estructura.

Recorre una lista de interfaces y los agrega como clases base y como la información necesaria para habilitar esta plantilla `QueryInterface`.

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Name                                                    | Descripción
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Obtiene un puntero al identificador de interfaz especificado.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Obtiene un puntero subyacente `IUnknown` interfaz actual `Implements` estructura.
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.
[ImplementsHelper::IidCount](#iidcount)                 | Contiene el número de identificadores de interfaz implementada en el actual `Implements` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ImplementsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="cancastto"></a>ImplementsHelper::CanCastTo

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Referencia a un identificador de interfaz.

*ppv*<br/>
Si esta operación se realiza correctamente, un puntero a la interfaz especificada por *riid* o *iid*.

*iid*<br/>
Referencia a un identificador de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Obtiene un puntero al identificador de interfaz especificado.

## <a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Puntero subyacente `IUnknown` interfaz.

### <a name="remarks"></a>Comentarios

Obtiene un puntero subyacente `IUnknown` interfaz actual `Implements` estructura.

## <a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se complete esta operación, *índice* se incrementa en 1.

*iids*<br/>
Una matriz de tipo IID.

### <a name="remarks"></a>Comentarios

Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.

## <a name="iidcount"></a>ImplementsHelper::IidCount

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Comentarios

Contiene el número de identificadores de interfaz implementada en el actual `Implements` objeto.
