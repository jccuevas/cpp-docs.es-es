---
title: HandleT (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: f66fbe23c305be15e09928242175dfa7ce8c141b
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821823"
---
# <a name="handlet-class"></a>HandleT (clase)

Representa un identificador de un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parameters

*HandleTraits*<br/>
Instancia de la estructura [handletraits (](handletraits-structure.md) que define las características comunes de un identificador.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Typedefs públicos

Name     | Descripción
-------- | -----------------------------
`Traits` | Sinónimo de `HandleTraits`.

### <a name="public-constructors"></a>Constructores públicos

Name                                | Descripción
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Inicializa una nueva instancia de la clase `HandleT` .
[HandleT::~HandleT](#tilde-handlet) | Desinicializa una instancia de la clase `HandleT`.

### <a name="public-methods"></a>Métodos públicos

Name                         | Descripción
---------------------------- | ----------------------------------------------------------------------
[HandleT::Attach](#attach)   | Asocia el identificador especificado al objeto `HandleT` actual.
[HandleT::Close](#close)     | Cierra el actual objeto `HandleT`.
[HandleT::Detach](#detach)   | Desasocia el objeto de `HandleT` actual de su identificador subyacente.
[HandleT::Get](#get)         | Obtiene el valor del identificador subyacente.
[HandleT::IsValid](#isvalid) | Indica si el objeto `HandleT` actual representa un identificador.

### <a name="protected-methods"></a>Métodos protegidos

Name                                     | Descripción
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Cierra el actual objeto `HandleT`.

### <a name="public-operators"></a>Operadores públicos

Name                                   | Descripción
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operator=](#operator-assign) | Mueve el valor del objeto `HandleT` especificado al objeto `HandleT` actual.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Name                        | Descripción
--------------------------- | ----------------------------------------------------------------
[HandleT::handle_](#handle) | Contiene el identificador representado por el objeto `HandleT`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HandleT`

## <a name="requirements"></a>Requisitos de

**Encabezado:** corewrappers. h

**Espacio de nombres:** Microsoft:: WRL:: wrappers

## <a name="tilde-handlet"></a>HandleT::~HandleT

Desinicializa una instancia de la clase `HandleT`.

```cpp
~HandleT();
```

## <a name="attach"></a>HandleT::Attach

Asocia el identificador especificado al objeto `HandleT` actual.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parameters

*h*<br/>
Identificador.

## <a name="close"></a>HandleT::Close

Cierra el actual objeto `HandleT`.

```cpp
void Close();
```

### <a name="remarks"></a>Notas

El identificador subyacente al `HandleT` actual está cerrado y el `HandleT` se establece en el estado no válido.

Si el identificador no se cierra correctamente, se produce una excepción en el subproceso que realiza la llamada.

## <a name="detach"></a>HandleT::Detach

Desasocia el objeto de `HandleT` actual de su identificador subyacente.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador subyacente.

### <a name="remarks"></a>Notas

Cuando se completa esta operación, el `HandleT` actual se establece en el estado no válido.

## <a name="get"></a>HandleT::Get

Obtiene el valor del identificador subyacente.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador.

## <a name="handle"></a>HandleT::handle_

Contiene el identificador representado por el objeto `HandleT`.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>HandleT::HandleT

Inicializa una nueva instancia de la clase `HandleT` .

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parameters

*h*<br/>
Identificador.

### <a name="remarks"></a>Notas

El primer constructor inicializa un objeto `HandleT` que no es un identificador válido para un objeto. El segundo constructor crea un nuevo objeto `HandleT` a partir del parámetro *h*.

## <a name="internalclose"></a>HandleT::InternalClose

Cierra el actual objeto `HandleT`.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valor devuelto

**true** si el `HandleT` actual se cerró correctamente; en caso contrario, **false**.

### <a name="remarks"></a>Notas

El valor de `InternalClose()` es `protected`.

## <a name="isvalid"></a>HandleT::IsValid

Indica si el objeto `HandleT` actual representa un identificador.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el `HandleT` representa un identificador; en caso contrario, **false**.

## <a name="operator-assign"></a>HandleT::operator=

Mueve el valor del objeto `HandleT` especificado al objeto `HandleT` actual.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parameters

*h*<br/>
Una referencia de valor r a un identificador.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de `HandleT` actual.

### <a name="remarks"></a>Notas

Esta operación invalida el `HandleT` objeto especificado por el parámetro *h*.
