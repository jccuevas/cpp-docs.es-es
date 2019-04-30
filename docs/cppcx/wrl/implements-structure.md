---
title: Implements (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 63cac6931428644cc5ddec7d87e49007e95e039d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398256"
---
# <a name="implements-structure"></a>Implements (estructura)

Implementa `QueryInterface` y `GetIid` para las interfaces especificadas.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>Parámetros

*I0*<br/>
El identificador de interfaz de cero. (Obligatorio)

*I1*<br/>
El primer identificador de interfaz. (Opcional)

*I2*<br/>
El segundo identificador de interfaz. (Opcional)

*I3*<br/>
El tercer identificador de interfaz. (Opcional)

*I4*<br/>
El cuarto identificador de interfaz. (Opcional)

*I5*<br/>
El quinto identificador de interfaz. (Opcional)

*I6*<br/>
El sexto ID de interfaz. (Opcional)

*I7*<br/>
El séptimo ID de interfaz. (Opcional)

*I8*<br/>
El identificador de identificador de octava interfaz. (Opcional)

*I9*<br/>
El noveno ID de interfaz. (Opcional)

*flags*<br/>
Marcas de configuración para la clase. Uno o varios [RuntimeClassType](runtimeclasstype-enumeration.md) enumeraciones que se especifican en un [RuntimeClassFlags](runtimeclassflags-structure.md) estructura.

## <a name="remarks"></a>Comentarios

Se deriva de la lista de interfaces especificadas e implementa las plantillas de aplicación auxiliar para `QueryInterface` y `GetIid`.

Cada *I0* a través de *I9* parámetro de interfaz debe derivarse de o `IUnknown`, `IInspectable`, o el [ChainInterfaces](chaininterfaces-structure.md) plantilla. El *marcas* parámetro determina si el soporte técnico se genera para `IUnknown` o `IInspectable`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

| Name        | Descripción                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Sinónimo de `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Métodos protegidos

| Name                                              | Descripción                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::CanCastTo](#cancastto)               | Obtiene un puntero a la interfaz especificada.                                                                    |
| [Implements::CastToUnknown](#casttounknown)       | Obtiene un puntero subyacente `IUnknown` interfaz.                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado. |

### <a name="protected-constants"></a>Constantes protegidas

| Name                              | Descripción                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | Contiene el número de identificadores de interfaz implementado. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="cancastto"></a>Implements::CanCastTo

Obtiene un puntero a la interfaz especificada.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Una referencia a un identificador de interfaz.

*ppv*<br/>
Si es correcto, un puntero a la interfaz especificada por *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un HRESULT que indica el error, como E_NOINTERFACE.

### <a name="remarks"></a>Comentarios

Se trata de una función auxiliar interna que realiza una operación de QueryInterface.

## <a name="casttounknown"></a>Implements::CastToUnknown

Obtiene un puntero subyacente `IUnknown` interfaz.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Esta operación siempre se realiza correctamente y devuelve el `IUnknown` puntero.

### <a name="remarks"></a>Comentarios

Función auxiliar interno.

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

Inserta el Id. de interfaz especificado por el parámetro de plantilla actual de cero en el elemento de matriz especificado.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parámetros

*index*<br/>
Índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se complete esta operación, *índice* se incrementa en 1.

*iids*<br/>
Una matriz de tipo IID.

### <a name="remarks"></a>Comentarios

Función auxiliar interno.

## <a name="iidcount"></a>Implements::IidCount

Contiene el número de identificadores de interfaz implementado.

```cpp
static const unsigned long IidCount;
```
