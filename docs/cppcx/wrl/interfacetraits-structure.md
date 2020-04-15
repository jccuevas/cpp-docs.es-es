---
title: InterfaceTraits (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371370"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parámetros

*I0*<br/>
El nombre de una interfaz.

*CloakedType*<br/>
Para `RuntimeClass` `Implements` , `ChainInterfaces`y , una interfaz que no estará en la lista de iDs de interfaz admitidos.

## <a name="remarks"></a>Observaciones

Implementa características comunes de una interfaz.

La segunda plantilla es una especialización para interfaces ocultas. La tercera plantilla es una especialización para parámetros Nil.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Tipos públicos

Nombre   | Descripción
------ | ------------------------------------------
`Base` | Sinónimo del parámetro de plantilla *I0.*

### <a name="public-methods"></a>Métodos públicos

Nombre                                                   | Descripción
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Indica si el puntero especificado se puede `Base`convertir en un puntero a .
[InterfaceTraits::CastToBase](#casttobase)             | Convierte el puntero especificado a `Base`un puntero a .
[InterfaceTraits::CastToUnknown](#casttounknown)       | Convierte el puntero especificado a `IUnknown`un puntero a .
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Asigna el identificador `Base` de interfaz al elemento de matriz especificado por el argumento index.
[InterfaceTraits::Verificar](#verify)                     | Comprueba que `Base` se deriva correctamente.

### <a name="public-constants"></a>Constantes públicas

Nombre                                   | Descripción
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Contiene el número de identificadores de `InterfaceTraits` interfaz asociados al objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits::CanCastTo

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*Ptr*<br/>
El nombre de un puntero a un tipo.

*riid*<br/>
El ID `Base`de interfaz de .

*Ppv*<br/>
Si esta operación se realiza correctamente, *ppv* apunta a la interfaz especificada por `Base`. De lo contrario, `nullptr` *ppv* se establece en .

### <a name="return-value"></a>Valor devuelto

**true** si esta operación es correcta y `Base` *ptr* se convierte en un puntero a ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Indica si el puntero especificado se puede `Base`convertir en un puntero a .

Para obtener `Base`más información acerca de , consulte la sección [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits::CastToBase

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de parámetro *ptr*.

*Ptr*<br/>
Puntero a un tipo *T*.

### <a name="return-value"></a>Valor devuelto

Puntero a `Base`.

### <a name="remarks"></a>Observaciones

Convierte el puntero especificado a `Base`un puntero a .

Para obtener `Base`más información acerca de , consulte la sección [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de parámetro *ptr*.

*Ptr*<br/>
Puntero al tipo *T*.

### <a name="return-value"></a>Valor devuelto

Puntero a la IUnknown de la que `Base` se deriva.

### <a name="remarks"></a>Observaciones

Convierte el puntero especificado a `IUnknown`un puntero a .

Para obtener `Base`más información acerca de , consulte la sección [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parámetros

*índice*<br/>
Puntero a un campo que contiene un valor de índice de base cero.

*iids*<br/>
Una matriz de interfaces.

### <a name="remarks"></a>Observaciones

Asigna el identificador `Base` de interfaz al elemento de matriz especificado por el argumento index.

Contrariamente al nombre de esta API, solo se modifica un elemento de matriz; no toda la matriz.

Para obtener `Base`más información acerca de , consulte la sección [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits::IidCount

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Observaciones

Contiene el número de identificadores de `InterfaceTraits` interfaz asociados al objeto actual.

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits::Verificar

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Observaciones

Comprueba que `Base` se deriva correctamente.

Para obtener `Base`más información acerca de , consulte la sección [Public Typedefs.](#public-typedefs)
