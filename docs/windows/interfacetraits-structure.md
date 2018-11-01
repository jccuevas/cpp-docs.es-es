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
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543954"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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
Para `RuntimeClass`, `Implements` y `ChainInterfaces`, admite la interfaz que no estará en la lista de identificadores de interfaz.

## <a name="remarks"></a>Comentarios

Características comunes de implementa de una interfaz.

La segunda plantilla es una especialización para interfaces encubiertas. La tercera plantilla es una especialización para parámetros Nil.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

nombre   | Descripción
------ | ------------------------------------------
`Base` | Un sinónimo para el *I0* parámetro de plantilla.

### <a name="public-methods"></a>Métodos públicos

Name                                                   | Descripción
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[Interfacetraits](#cancastto)               | Indica si el puntero especificado se puede convertir en un puntero a `Base`.
[Casttobase](#casttobase)             | Convierte el puntero especificado a un puntero a `Base`.
[Interfacetraits](#casttounknown)       | Convierte el puntero especificado a un puntero a `IUnknown`.
[Interfacetraits](#fillarraywithiid) | Asigna el identificador de interfaz de `Base` al elemento de matriz especificado por el argumento de índice.
[Interfacetraits](#verify)                     | Comprueba que `Base` se deriva correctamente.

### <a name="public-constants"></a>Constantes públicas

nombre                                   | Descripción
-------------------------------------- | ---------------------------------------------------------------------------------------
[Interfacetraits](#iidcount) | Contiene el número de identificadores asociados con la actual interfaz `InterfaceTraits` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InterfaceTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="cancastto"></a>Interfacetraits

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
El nombre de un puntero a un tipo.

*riid*<br/>
El identificador de interfaz de `Base`.

*PPV*<br/>
Si esta operación se realiza correctamente, *ppv* apunta a la interfaz especificada por `Base`. En caso contrario, *ppv* está establecido en `nullptr`.

### <a name="return-value"></a>Valor devuelto

**True** si esta operación se realiza correctamente y *ptr* se convierte en un puntero a `Base`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Indica si el puntero especificado se puede convertir en un puntero a `Base`.

Para obtener más información acerca de `Base`, consulte el [Typedefs pública](#public-typedefs) sección.

## <a name="casttobase"></a>Casttobase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de parámetro *ptr*.

*ptr*<br/>
Puntero a un tipo *T*.

### <a name="return-value"></a>Valor devuelto

Un puntero a `Base`.

### <a name="remarks"></a>Comentarios

Convierte el puntero especificado a un puntero a `Base`.

Para obtener más información acerca de `Base`, consulte el [Typedefs pública](#public-typedefs) sección.

## <a name="casttounknown"></a>Interfacetraits

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de parámetro *ptr*.

*ptr*<br/>
Puntero al tipo *T*.

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz IUnknown del que `Base` derivada.

### <a name="remarks"></a>Comentarios

Convierte el puntero especificado a un puntero a `IUnknown`.

Para obtener más información acerca de `Base`, consulte el [Typedefs pública](#public-typedefs) sección.

## <a name="fillarraywithiid"></a>Interfacetraits

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Puntero a un campo que contiene un valor de índice de base cero.

*IID*<br/>
Una matriz de identificadores de interfaz.

### <a name="remarks"></a>Comentarios

Asigna el identificador de interfaz de `Base` al elemento de matriz especificado por el argumento de índice.

Al contrario que el nombre de esta API, se modifica el elemento de solo matriz; no toda la matriz.

Para obtener más información acerca de `Base`, consulte el [Typedefs pública](#public-typedefs) sección.

## <a name="iidcount"></a>Interfacetraits

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Comentarios

Contiene el número de identificadores asociados con la actual interfaz `InterfaceTraits` objeto.

## <a name="verify"></a>Interfacetraits

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Comentarios

Comprueba que `Base` se deriva correctamente.

Para obtener más información acerca de `Base`, consulte el [Typedefs pública](#public-typedefs) sección.
