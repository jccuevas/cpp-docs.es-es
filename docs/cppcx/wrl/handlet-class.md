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
ms.openlocfilehash: 6e5824da03fb85e52f413f5678ea6e0fd6c77ddd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786059"
---
# <a name="handlet-class"></a>HandleT (clase)

Representa un identificador a un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parámetros

*HandleTraits*<br/>
Una instancia de la [HandleTraits](handletraits-structure.md) una estructura que define las características comunes de un controlador.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name     | Descripción
-------- | -----------------------------
`Traits` | Sinónimo de `HandleTraits`.

### <a name="public-constructors"></a>Constructores públicos

Name                                | Descripción
----------------------------------- | --------------------------------------------------
[HandleT::HandleT](#handlet)        | Inicializa una nueva instancia de la clase `HandleT`.
[HandleT::~HandleT](#tilde-handlet) | Desinicializa una instancia de la `HandleT` clase.

### <a name="public-methods"></a>Métodos públicos

Name                         | Descripción
---------------------------- | ----------------------------------------------------------------------
[HandleT::Attach](#attach)   | Asocia el identificador especificado con el actual `HandleT` objeto.
[HandleT::Close](#close)     | Cierra el actual objeto `HandleT`.
[HandleT::Detach](#detach)   | Desasocia actual `HandleT` objeto a partir de su identificador subyacente.
[HandleT::Get](#get)         | Obtiene el valor del identificador subyacente.
[HandleT::IsValid](#isvalid) | Indica si el actual `HandleT` objeto representa un identificador.

### <a name="protected-methods"></a>Métodos protegidos

Name                                     | Descripción
---------------------------------------- | ------------------------------------
[HandleT::InternalClose](#internalclose) | Cierra el actual objeto `HandleT`.

### <a name="public-operators"></a>Operadores públicos

Name                                   | Descripción
-------------------------------------- | ----------------------------------------------------------------------------------
[HandleT::operator=](#operator-assign) | Mueve el valor del elemento especificado `HandleT` el objeto actual `HandleT` objeto.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Name                        | Descripción
--------------------------- | ----------------------------------------------------------------
[HandleT::handle_](#handle) | Contiene el identificador representado por la `HandleT` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HandleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="tilde-handlet"></a>HandleT::~HandleT

Desinicializa una instancia de la `HandleT` clase.

```cpp
~HandleT();
```

## <a name="attach"></a>HandleT::Attach

Asocia el identificador especificado con el actual `HandleT` objeto.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Un identificador.

## <a name="close"></a>HandleT::Close

Cierra el actual objeto `HandleT`.

```cpp
void Close();
```

### <a name="remarks"></a>Comentarios

El identificador que subyace a actual `HandleT` está cerrado y el `HandleT` se establece en el estado no válido.

Si el identificador no se cierra correctamente, se produce una excepción en el subproceso de llamada.

## <a name="detach"></a>HandleT::Detach

Desasocia actual `HandleT` objeto a partir de su identificador subyacente.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Valor devuelto

El identificador subyacente.

### <a name="remarks"></a>Comentarios

Cuando finalice esta operación, actual `HandleT` está establecido en el estado no válido.

## <a name="get"></a>HandleT::Get

Obtiene el valor del identificador subyacente.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador.

## <a name="handle"></a>HandleT::handle_

Contiene el identificador representado por la `HandleT` objeto.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>HandleT::HandleT

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

*h*<br/>
Un identificador.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa un `HandleT` objeto que no es un identificador válido para un objeto. El segundo constructor crea un nuevo `HandleT` objeto de parámetro *h*.

## <a name="internalclose"></a>HandleT::InternalClose

Cierra el actual objeto `HandleT`.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Valor devuelto

**True** si actual `HandleT` cerrado correctamente; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

El valor de `InternalClose()` es `protected`.

## <a name="isvalid"></a>HandleT::IsValid

Indica si el actual `HandleT` objeto representa un identificador.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el `HandleT` representa un identificador; en caso contrario, **false**.

## <a name="operator-assign"></a>HandleT::operator=

Mueve el valor del elemento especificado `HandleT` el objeto actual `HandleT` objeto.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Una referencia rvalue a un identificador.

### <a name="return-value"></a>Valor devuelto

Una referencia a la actual `HandleT` objeto.

### <a name="remarks"></a>Comentarios

Esta operación invalida la `HandleT` objeto especificado por el parámetro *h*.
