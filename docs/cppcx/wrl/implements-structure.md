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
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371406"
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
El ID de interfaz cero. (Obligatorio)

*I1*<br/>
El primer ID de interfaz. (Opcional)

*I2*<br/>
El segundo ID de interfaz. (Opcional)

*I3*<br/>
El tercer ID de interfaz. (Opcional)

*I4*<br/>
El cuarto ID de interfaz. (Opcional)

*I5*<br/>
El quinto ID de interfaz. (Opcional)

*I6*<br/>
El sexto ID de interfaz. (Opcional)

*I7*<br/>
El séptimo ID de interfaz. (Opcional)

*I8*<br/>
El octavo ID de interfaz. (Opcional)

*I9*<br/>
El noveno ID de interfaz. (Opcional)

*Banderas*<br/>
Indicadores de configuración para la clase. Una o más [enumeraciones RuntimeClassType](runtimeclasstype-enumeration.md) que se especifican en un [RuntimeClassFlags](runtimeclassflags-structure.md) estructura.

## <a name="remarks"></a>Observaciones

Deriva de la lista de interfaces especificadas `QueryInterface` e `GetIid`implementa plantillas auxiliares para e .

Cada parámetro de interfaz *I0* `IUnknown`a `IInspectable` *I9* debe derivar de la plantilla , , o [ChainInterfaces.](chaininterfaces-structure.md) El parámetro *flags* determina si se `IUnknown` `IInspectable`genera compatibilidad para o .

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

| Nombre        | Descripción                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Sinónimo de `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Métodos protegidos

| Nombre                                              | Descripción                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implementa::CanCastTo](#cancastto)               | Obtiene un puntero a la interfaz especificada.                                                                    |
| [Implementa::CastToUnknown](#casttounknown)       | Obtiene un puntero a `IUnknown` la interfaz subyacente.                                                        |
| [Implementa::FillArrayWithIid](#fillarraywithiid) | Inserta el identificador de interfaz especificado por el parámetro de plantilla cero actual en el elemento de matriz especificado. |

### <a name="protected-constants"></a>Constantes protegidas

| Nombre                              | Descripción                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implementa::IidCount](#iidcount) | Contiene el número de iDs de interfaz implementados. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>Implementa::CanCastTo

Obtiene un puntero a la interfaz especificada.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parámetros

*riid*<br/>
Una referencia a un ID de interfaz.

*Ppv*<br/>
Si se realiza correctamente, un puntero a la interfaz especificada por *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error, como E_NOINTERFACE.

### <a name="remarks"></a>Observaciones

Se trata de una función auxiliar interna que realiza una operación QueryInterface.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>Implementa::CastToUnknown

Obtiene un puntero a `IUnknown` la interfaz subyacente.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Esta operación siempre se `IUnknown` realiza correctamente y devuelve el puntero.

### <a name="remarks"></a>Observaciones

Función auxiliar interna.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>Implementa::FillArrayWithIid

Inserta el identificador de interfaz especificado por el parámetro de plantilla cero actual en el elemento de matriz especificado.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parámetros

*índice*<br/>
Un índice de base cero que indica el elemento de matriz inicial para esta operación. Cuando se completa esta operación, *index* se incrementa en 1.

*iids*<br/>
Matriz de tipo IID.

### <a name="remarks"></a>Observaciones

Función auxiliar interna.

## <a name="implementsiidcount"></a><a name="iidcount"></a>Implementa::IidCount

Contiene el número de iDs de interfaz implementados.

```cpp
static const unsigned long IidCount;
```
