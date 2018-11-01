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
ms.openlocfilehash: 87967f733cbb6ae2db999232c57751521d77fdc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552703"
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
(Obligatorio) Id. de interfaz 0.

*I1*<br/>
(Obligatorio) Id. de interfaz 1.

*I2*<br/>
(Opcional) Id. de interfaz 2.

*I3*<br/>
(Opcional) Id. de interfaz 3.

*I4*<br/>
(Opcional) Id. de interfaz 4.

*I5*<br/>
(Opcional) Id. de interfaz 5.

*I6*<br/>
(Opcional) Id. de interfaz 6.

*I7*<br/>
(Opcional) Id. de interfaz 7.

*I8*<br/>
(Opcional) Id. de interfaz 8.

*I9*<br/>
(Opcional) Id. de interfaz 9.

*DerivedType*<br/>
Un tipo derivado.

*BaseType*<br/>
El tipo base de un tipo derivado.

*hasImplements*<br/>
Valor de un valor booleano que si **true**, significa que no se puede usar un [MixIn](../windows/mixin-structure.md) estructura con una clase que no se deriva de la [implementa](../windows/implements-structure.md) una estructura.

## <a name="members"></a>Miembros

### <a name="protected-methods"></a>Métodos protegidos

Name                                                   | Descripción
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Chaininterfaces](#cancastto)               | Indica si el identificador de interfaz especificado puede convertirse a cada una de las especializaciones definidas por el `ChainInterface` parámetros de plantilla.
[Chaininterfaces](#casttounknown)       | Convierte el puntero de interfaz del tipo definido por el *I0* parámetro de plantilla en un puntero a `IUnknown`.
[Chaininterfaces](#fillarraywithiid) | Almacena el identificador de interfaz definido por el *I0* parámetro de plantilla en una ubicación especificada en una matriz especificada de identificadores de interfaz.
[Chaininterfaces](#verify)                     | Comprueba que cada interfaz definida por los parámetros de plantilla *I0* a través de *I9* hereda `IUnknown` o `IInspectable`y que *I0* hereda de *I1* a través de *I9*.

### <a name="protected-constants"></a>Constantes protegidas

nombre                                   | Descripción
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[Chaininterfaces](#iidcount) | El número total de identificadores contenidos en las interfaces especificadas por los parámetros de plantilla de interfaz *I0* a través de *I9*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="cancastto"></a>Chaininterfaces

Indica si el identificador de interfaz especificado puede convertirse a cada una de las especializaciones definidas por los parámetros de plantilla no predeterminado.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Id. de interfaz.

*PPV*<br/>
Un puntero en el último identificador de interfaz que se convirtió correctamente.

### <a name="return-value"></a>Valor devuelto

**True** si todas las operaciones de conversión se realizó correctamente; en caso contrario, **false**.

## <a name="casttounknown"></a>Chaininterfaces

Convierte el puntero de interfaz del tipo definido por el *I0* parámetro de plantilla en un puntero a `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a `IUnknown`.

## <a name="fillarraywithiid"></a>Chaininterfaces

Almacena el identificador de interfaz definido por el *I0* parámetro de plantilla en una ubicación especificada en una matriz especificada de identificadores de interfaz.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Puntero a un valor de índice en el *IID* matriz.

*IID*<br/>
Una matriz de identificadores de interfaz.

## <a name="iidcount"></a>Chaininterfaces

El número total de identificadores contenidos en las interfaces especificadas por los parámetros de plantilla de interfaz *I0* a través de *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Valor devuelto

El número total de identificadores de interfaz.

### <a name="remarks"></a>Comentarios

Parámetros de plantilla *I0* y *I1* son necesarios y los parámetros *I2* a través de *I9* son opcionales. El recuento IID de cada interfaz suele ser 1.

## <a name="verify"></a>Chaininterfaces

Comprueba que cada interfaz definida por los parámetros de plantilla *I0* a través de *I9* hereda `IUnknown` o `IInspectable`y que *I0* hereda de *I1* a través de *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Comentarios

Si se produce un error en la operación de comprobación, un `static_assert` emite un mensaje de error que describe el error.

Parámetros de plantilla *I0* y *I1* son necesarios y los parámetros *I2* a través de *I9* son opcionales.
