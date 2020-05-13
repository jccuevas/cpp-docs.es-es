---
title: Platform::Box (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
ms.openlocfilehash: 7484bcda3f05a8a9e56a33222d0630d4597e1219
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354758"
---
# <a name="platformbox-class"></a>Platform::Box (Clase)

Habilita un tipo de valor como `Windows::Foundation::DateTime` o un tipo escalar como `int` para almacenarlo en un tipo `Platform::Object` . Normalmente no es necesario usar `Box` explícitamente porque la conversión boxing se produce de manera implícita cuando se convierte un tipo de valor a `Object^`.

### <a name="syntax"></a>Sintaxis

```cpp
ref class Box abstract;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** vccorlib.h

**Espacio de nombres:** Platform

### <a name="members"></a>Miembros

|Member|Descripción|
|------------|-----------------|
|[Box](#ctor) | Crea un `Box` que puede encapsular un valor del tipo especificado. |
|[operador&lt;Box const T&gt;^](#box-const-t) | Permite conversiones boxing de una clase de valor `const``T` o de una clase `enum``T` en `Box<T>`. |
|[operador&lt;Box const volatile T&gt;^](#box-const-volatile-t) | Permite conversiones boxing de una clase de valor `const volatile``T` o de un tipo `enum``T` en `Box<T>`. |
|[operador&lt;Caja T&gt;^](#box-t) | Permite conversiones boxing de una clase de valor `T` en `Box<T>`. |
|[operador&lt;Caja volátil T&gt;^](#box-volatile-t) | Permite conversiones boxing de una clase de valor `volatile``T` o de un tipo `enum``T` en `Box<T>`. |
|[Caja::operador T](#t) | Permite conversiones boxing de una clase de valor `T` o de una clase `enum``T` en `Box<T>`. |
|[Propiedad de valor](#value) | Devuelve el valor encapsulado en el objeto `Box`. |

## <a name="boxbox-constructor"></a><a name="ctor"></a>Box::Box Constructor

Crea un `Box` que puede encapsular un valor del tipo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
Box(T valueArg);
```

### <a name="parameters"></a>Parámetros

*valueArg*<br/>
Tipo de valor del que se va a realizar la conversión boxing, por ejemplo, `int`, `bool`, `float64`, `DateTime`.

## <a name="boxoperator-boxltconst-tgt-operator"></a><a name="box-const-t"></a>Box::operator&lt;Box const T&gt;- Operador

Permite conversiones boxing de una clase de valor `const``T` o de una clase `enum``T` en `Box<T>`.

### <a name="syntax"></a>Sintaxis

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Cualquier valor de clase, struct de valor o tipo de enumeración. Incluye los tipos integrados en el espacio de [nombres predeterminado.](../cppcx/default-namespace.md)

### <a name="return-value"></a>Valor devuelto

Instancia `Platform::Box<T>^` que representa el valor original en caja en una clase ref.

## <a name="boxoperator-boxltconst-volatile-tgt-operator"></a><a name="box-const-volatile-t"></a>Box::operator&lt;Box const&gt;volatile T - Operador

Permite conversiones boxing de una clase de valor `const volatile``T` o de un tipo `enum``T` en `Box<T>`.

### <a name="syntax"></a>Sintaxis

```cpp
operator Box<const volatile T>^(const volatile T valueType);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el espacio de [nombres predeterminado.](../cppcx/default-namespace.md)

### <a name="return-value"></a>Valor devuelto

Instancia `Platform::Box<T>^` que representa el valor original en caja en una clase ref.

## <a name="boxoperator-boxlttgt-operator"></a><a name="box-t"></a>Box::operador&lt;Caja&gt;T - Operador

Permite conversiones boxing de una clase de valor `T` en `Box<T>`.

### <a name="syntax"></a>Sintaxis

```cpp
operator Box<const T>^(const T valueType);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el espacio de [nombres predeterminado.](../cppcx/default-namespace.md)

### <a name="return-value"></a>Valor devuelto

Instancia `Platform::Box<T>^` que representa el valor original en caja en una clase ref.

## <a name="boxoperator-boxltvolatile-tgt-operator"></a><a name="box-volatile-t"></a>Box::operator&lt;Box&gt;volatile T - Operador

Permite conversiones boxing de una clase de valor `volatile``T` o de un tipo `enum``T` en `Box<T>`.

### <a name="syntax"></a>Sintaxis

```cpp
operator Box<volatile T>^(volatile T valueType);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el espacio de [nombres predeterminado.](../cppcx/default-namespace.md)

### <a name="return-value"></a>Valor devuelto

Instancia `Platform::Box<T>^` que representa el valor original en caja en una clase ref.

## <a name="boxoperator-t-operator"></a><a name="t"></a>Box::operador T Operador

Permite conversiones boxing de una clase de valor `T` o de una clase `enum``T` en `Box<T>`.

### <a name="syntax"></a>Sintaxis

```cpp
operator Box<T>^(T valueType);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el espacio de [nombres predeterminado.](../cppcx/default-namespace.md)

### <a name="return-value"></a>Valor devuelto

Instancia `Platform::Box<T>^` que representa el valor original en caja en una clase ref.

## <a name="boxvalue-property"></a><a name="value"></a>Propiedad Box::Value

Devuelve el valor encapsulado en el objeto `Box`.

### <a name="syntax"></a>Sintaxis

```cpp
virtual property T Value{
   T get();
}
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor al que se le ha aplicado la conversión boxing con el mismo tipo que tenía originalmente antes de que se le aplicara esa conversión.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)<br/>
[Conversión boxing](../cppcx/boxing-c-cx.md)
