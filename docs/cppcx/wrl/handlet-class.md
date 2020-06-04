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
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371464"
---
# <a name="handlet-class"></a>HandleT (clase)

Representa un identificador de un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parámetros

*HandleTraits*<br/>
Instancia de la [HandleTraits](handletraits-structure.md) estructura que define las características comunes de un identificador.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre     | Descripción
-------- | -----------------------------
`Traits` | Sinónimo de `HandleTraits`.

### <a name="public-constructors"></a>Constructores públicos

Nombre                                | Descripción
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Inicializa una nueva instancia de la clase `HandleT`.
[HandleT::-HandleT](#tilde-handlet) | Desinicializa una instancia `HandleT` de la clase.

### <a name="public-methods"></a>Métodos públicos

Nombre                         | Descripción
---------------------------- | ----------------------------------------------------------------------
[HandleT::Adjuntar](#attach)   | Asocia el identificador especificado `HandleT` con el objeto actual.
[HandleT::Cerrar](#close)     | Cierra el actual objeto `HandleT`.
[HandleT::Dsetach](#detach)   | Desasocia el `HandleT` objeto actual de su identificador subyacente.
[HandleT::Get](#get)         | Obtiene el valor del identificador subyacente.
[HandleT::IsValid](#isvalid) | Indica si el `HandleT` objeto actual representa un identificador.

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                     | Descripción
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Cierra el actual objeto `HandleT`.

### <a name="public-operators"></a>Operadores públicos

Nombre                                   | Descripción
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operador ?](#operator-assign) | Mueve el valor del `HandleT` objeto especificado `HandleT` al objeto actual.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                        | Descripción
--------------------------- | ----------------------------------------------------------------
[HandleT::handle_](#handle) | Contiene el identificador representado por `HandleT` el objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HandleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>HandleT::-HandleT

Desinicializa una instancia `HandleT` de la clase.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>HandleT::Adjuntar

Asocia el identificador especificado `HandleT` con el objeto actual.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Un identificador.

## <a name="handletclose"></a><a name="close"></a>HandleT::Cerrar

Cierra el actual objeto `HandleT`.

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

El identificador que subyace a la corriente `HandleT` se cierra y `HandleT` se establece en el estado no válido.

Si el identificador no se cierra correctamente, se genera una excepción en el subproceso que realiza la llamada.

## <a name="handletdetach"></a><a name="detach"></a>HandleT::Dsetach

Desasocia el `HandleT` objeto actual de su identificador subyacente.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valor devuelto

El identificador subyacente.

### <a name="remarks"></a>Observaciones

Cuando se completa esta `HandleT` operación, la corriente se establece en el estado no válido.

## <a name="handletget"></a><a name="get"></a>HandleT::Get

Obtiene el valor del identificador subyacente.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador.

## <a name="handlethandle_"></a><a name="handle"></a>HandleT::handle_

Contiene el identificador representado por `HandleT` el objeto.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>HandleT::HandleT

Inicializa una nueva instancia de la clase `HandleT`.

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Un identificador.

### <a name="remarks"></a>Observaciones

El primer constructor `HandleT` inicializa un objeto que no es un identificador válido para un objeto. El segundo constructor `HandleT` crea un nuevo objeto a partir del parámetro *h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a>HandleT::InternalClose

Cierra el actual objeto `HandleT`.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valor devuelto

**true** si `HandleT` la corriente se cerró correctamente; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

`InternalClose()` es `protected`.

## <a name="handletisvalid"></a><a name="isvalid"></a>HandleT::IsValid

Indica si el `HandleT` objeto actual representa un identificador.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si `HandleT` el representa un identificador; de lo contrario, **false**.

## <a name="handletoperator"></a><a name="operator-assign"></a>HandleT::operador ?

Mueve el valor del `HandleT` objeto especificado `HandleT` al objeto actual.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Una referencia rvalue a un identificador.

### <a name="return-value"></a>Valor devuelto

Una referencia al `HandleT` objeto actual.

### <a name="remarks"></a>Observaciones

Esta operación invalida el objeto especificado por el `HandleT` parámetro *h*.
