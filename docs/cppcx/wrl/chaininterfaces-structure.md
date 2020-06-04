---
title: ChainInterfaces (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372661"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces (estructura)

Especifica las funciones de comprobación e inicialización que se pueden aplicar a un conjunto de identificadores de interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>Parámetros

*I0*<br/>
(Obligatorio) ID de interfaz 0.

*I1*<br/>
(Obligatorio) ID de interfaz 1.

*I2*<br/>
(Opcional) ID de interfaz 2.

*I3*<br/>
(Opcional) ID de interfaz 3.

*I4*<br/>
(Opcional) ID de interfaz 4.

*I5*<br/>
(Opcional) ID de interfaz 5.

*I6*<br/>
(Opcional) Id. de interfaz 6.

*I7*<br/>
(Opcional) ID de interfaz 7.

*I8*<br/>
(Opcional) ID de interfaz 8.

*I9*<br/>
(Opcional) ID de interfaz 9.

*DerivedType*<br/>
Un tipo derivado.

*Basetype*<br/>
El tipo base de un tipo derivado.

*hasImplements*<br/>
Un valor booleano que si **true**, significa que no se puede usar una estructura [MixIn](mixin-structure.md) con una clase que no deriva de la stucture [Implements.](implements-structure.md)

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                                   | Descripción
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Indica si el identificador de interfaz especificado se puede convertir `ChainInterface` en cada una de las especializaciones definidas por los parámetros de plantilla.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Convierte el puntero de interfaz del tipo definido por `IUnknown`el parámetro de plantilla *I0* en un puntero a .
[ChainInterfaces::FillArrayWithIid](#fillarraywithiid) | Almacena el identificador de interfaz definido por el parámetro de plantilla *I0* en una ubicación especificada en una matriz especificada de identificadores de interfaz.
[ChainInterfaces::Verificar](#verify)                     | Comprueba que cada interfaz definida por los parámetros `IUnknown` de `IInspectable`plantilla *I0* a *I9* hereda de y/o , y que *I0* hereda de *I1* a *I9*.

### <a name="protected-constants"></a>Constantes protegidas

Nombre                                   | Descripción
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | El número total de ID de interfaz contenidos en las interfaces especificadas por los parámetros de plantilla *I0* a *I9.*

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces::CanCastTo

Indica si el identificador de interfaz especificado se puede convertir en cada una de las especializaciones definidas por los parámetros de plantilla no predeterminados.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*Ppv*<br/>
Puntero al último identificador de interfaz que se ha emitido correctamente.

### <a name="return-value"></a>Valor devuelto

**true** si todas las operaciones de conversión se realizaron correctamente; de lo contrario, **false**.

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Convierte el puntero de interfaz del tipo definido por `IUnknown`el parámetro de plantilla *I0* en un puntero a .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Puntero a `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithIid

Almacena el identificador de interfaz definido por el parámetro de plantilla *I0* en una ubicación especificada en una matriz especificada de identificadores de interfaz.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parámetros

*índice*<br/>
Puntero a un valor de índice en la matriz *iids.*

*iids*<br/>
Una matriz de interfaces.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces::IidCount

El número total de ID de interfaz contenidos en las interfaces especificadas por los parámetros de plantilla *I0* a *I9.*

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Valor devuelto

El número total de interfaces.

### <a name="remarks"></a>Observaciones

Los parámetros de plantilla *I0* e *I1* son obligatorios y los parámetros *I2* a *I9* son opcionales. El recuento de IID de cada interfaz suele ser 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces::Verificar

Comprueba que cada interfaz definida por los parámetros `IUnknown` de `IInspectable`plantilla *I0* a *I9* hereda de y/o , y que *I0* hereda de *I1* a *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Observaciones

Si se produce un `static_assert` error en la operación de verificación, se emite un mensaje de error que describe el error.

Los parámetros de plantilla *I0* e *I1* son obligatorios y los parámetros *I2* a *I9* son opcionales.
