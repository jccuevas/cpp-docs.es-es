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
ms.openlocfilehash: 0ce6e9193107cbd0d033d99b257e41004b4343a8
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821862"
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

### <a name="parameters"></a>Parameters

*I0*<br/>
IDENTIFICADOR de la interfaz inicial. Obligación

*I1*<br/>
IDENTIFICADOR de la primera interfaz. (opcional)

*I2*<br/>
El segundo identificador de interfaz. (opcional)

*I3*<br/>
El tercer identificador de interfaz. (opcional)

*I4*<br/>
El cuarto identificador de interfaz. (opcional)

*I5*<br/>
El quinto identificador de interfaz. (opcional)

*I6*<br/>
Sexto identificador de interfaz. (opcional)

*I7*<br/>
Séptimo identificador de interfaz. (opcional)

*I8*<br/>
Octavo identificador de interfaz. (opcional)

*I9*<br/>
Noveno identificador de interfaz. (opcional)

*flags*<br/>
Marcas de configuración para la clase. Una o varias enumeraciones [runtimeclasstype (](runtimeclasstype-enumeration.md) que se especifican en una estructura [runtimeclassflags (](runtimeclassflags-structure.md) .

## <a name="remarks"></a>Notas

Deriva de la lista de interfaces especificadas e implementa plantillas auxiliares para `QueryInterface` y `GetIid`.

Cada parámetro de la interfaz *I0* a través de *i9* debe derivar de `IUnknown`, `IInspectable`o la plantilla [ChainInterfaces](chaininterfaces-structure.md) . El parámetro *Flags* determina si se ha generado compatibilidad para `IUnknown` o `IInspectable`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Typedefs públicos

| Name        | Descripción                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Sinónimo de `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Métodos protegidos

| Name                                              | Descripción                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::CanCastTo](#cancastto)               | Obtiene un puntero a la interfaz especificada.                                                                    |
| [Implements::CastToUnknown](#casttounknown)       | Obtiene un puntero a la interfaz de `IUnknown` subyacente.                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | Inserta el ID. de interfaz especificado por el parámetro de plantilla inicial actual en el elemento de matriz especificado. |

### <a name="protected-constants"></a>Constantes protegidas

| Name                              | Descripción                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | Contiene el número de identificadores de interfaz implementados. |

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Requisitos de

**Encabezado:** implementa. h

**Espacio de nombres:** Microsoft::WRL

## <a name="cancastto"></a>Implements::CanCastTo

Obtiene un puntero a la interfaz especificada.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameters

*riid*<br/>
Referencia a un identificador de interfaz.

*ppv*<br/>
Si es correcto, un puntero a la interfaz especificada por *riid*.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error, como E_NOINTERFACE.

### <a name="remarks"></a>Notas

Se trata de una función auxiliar interna que realiza una operación QueryInterface.

## <a name="casttounknown"></a>Implements::CastToUnknown

Obtiene un puntero a la interfaz de `IUnknown` subyacente.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valor devuelto

Esta operación siempre se realiza correctamente y devuelve el puntero `IUnknown`.

### <a name="remarks"></a>Notas

Función auxiliar interna.

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

Inserta el ID. de interfaz especificado por el parámetro de plantilla inicial actual en el elemento de matriz especificado.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameters

*index*<br/>
Índice de base cero que indica el elemento de matriz de inicio para esta operación. Cuando se completa esta operación, el *Índice* se incrementa en 1.

*iids*<br/>
Matriz de tipo IID.

### <a name="remarks"></a>Notas

Función auxiliar interna.

## <a name="iidcount"></a>Implements::IidCount

Contiene el número de identificadores de interfaz implementados.

```cpp
static const unsigned long IidCount;
```
