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
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371395"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parámetros

*RuntimeClassFlagsT*<br/>
Campo de indicadores que especifica uno o varios enumeradores [RuntimeClassType.](runtimeclasstype-enumeration.md)

*ILst*<br/>
Una lista de interfaces.

*IsDelegateToClass*<br/>
Especifique **true** si la `Implements` instancia actual de es una clase base del primer id de interfaz en *IL*; de lo contrario, **false**.

## <a name="remarks"></a>Observaciones

Ayuda a implementar la estructura [Implements.](implements-structure.md)

Esta plantilla atraviesa una lista de interfaces y las agrega `QueryInterface`como clases base y como información necesaria para habilitar .

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                                    | Descripción
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Obtiene un puntero al identificador de interfaz especificado.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Obtiene un puntero a `IUnknown` la interfaz `Implements` subyacente para la estructura actual.
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Inserta el identificador de interfaz especificado por el parámetro de plantilla cero actual en el elemento de matriz especificado.
[ImplementsHelper::IidCount](#iidcount)                 | Contiene el número de identificadores de interfaz implementados en el objeto actual. `Implements`

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ImplementsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper::CanCastTo

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

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
Referencia a un ID de interfaz.

*Ppv*<br/>
Si esta operación se realiza correctamente, un puntero a la interfaz especificada por *riid* o *iid*.

*Iid*<br/>
Referencia a un ID de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Observaciones

Obtiene un puntero al identificador de interfaz especificado.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la `IUnknown` interfaz subyacente.

### <a name="remarks"></a>Observaciones

Obtiene un puntero a `IUnknown` la interfaz `Implements` subyacente para la estructura actual.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parámetros

*índice*<br/>
Un índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se completa esta operación, *index* se incrementa en 1.

*iids*<br/>
Una matriz de ITV de tipo.

### <a name="remarks"></a>Observaciones

Inserta el identificador de interfaz especificado por el parámetro de plantilla cero actual en el elemento de matriz especificado.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper::IidCount

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Observaciones

Contiene el número de identificadores de interfaz implementados en el objeto actual. `Implements`
