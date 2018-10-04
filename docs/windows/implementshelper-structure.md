---
title: ImplementsHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 574d0dbf6a252f65dd6c15681a243ce0e4086f0e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788505"
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
Un campo de marcas que especifica uno o más [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) enumeradores.

*ILst*<br/>
Una lista de identificadores de interfaz.

*IsDelegateToClass*<br/>
Especificar `true` si la instancia actual de `Implements` es una clase base de la primera Id. de interfaz en *ILst*; en caso contrario, `false`.

## <a name="remarks"></a>Comentarios

Ayuda a implementar la [implementa](../windows/implements-structure.md) estructura.

Recorre una lista de interfaces y los agrega como clases base y como la información necesaria para habilitar esta plantilla `QueryInterface`.

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Name                                                    | Descripción
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Implementshelper](#cancastto)               | Obtiene un puntero al identificador de interfaz especificado.
[Implementshelper](#casttounknown)       | Obtiene un puntero subyacente `IUnknown` interfaz actual `Implements` estructura.
[Implementshelper](#fillarraywithiid) | Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.
[Implementshelper](#iidcount)                 | Contiene el número de identificadores de interfaz implementada en el actual `Implements` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ImplementsHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="cancastto"></a>Implementshelper

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

*PPV*<br/>
Si esta operación se realiza correctamente, un puntero a la interfaz especificada por *riid* o *iid*.

*IID*<br/>
Referencia a un identificador de interfaz.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

### <a name="remarks"></a>Comentarios

Obtiene un puntero al identificador de interfaz especificado.

## <a name="casttounknown"></a>Implementshelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Puntero subyacente `IUnknown` interfaz.

### <a name="remarks"></a>Comentarios

Obtiene un puntero subyacente `IUnknown` interfaz actual `Implements` estructura.

## <a name="fillarraywithiid"></a>Implementshelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se complete esta operación, *índice* se incrementa en 1.

*IID*<br/>
Una matriz de tipo IID.

### <a name="remarks"></a>Comentarios

Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.

## <a name="iidcount"></a>Implementshelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Comentarios

Contiene el número de identificadores de interfaz implementada en el actual `Implements` objeto.
