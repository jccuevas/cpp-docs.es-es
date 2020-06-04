---
title: error_category (Clase)
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 3ed2eceb60c2efa78181faea58a256b0e35d489f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076611"
---
# <a name="error_category-class"></a>error_category (Clase)

Representa la base común abstracta de objetos que describe una categoría de códigos de error.

## <a name="syntax"></a>Sintaxis

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Observaciones

Dos objetos predefinidos implementan `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) y [system_category](../standard-library/system-error-functions.md#system_category).

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|Tipo que representa el valor del código de error almacenado.|

### <a name="functions"></a>Functions

|||
|-|-|
|[default_error_condition](#default_error_condition)|Almacena el valor del código de error para un objeto de condición de error.|
|[equivalent](#equivalent)|Devuelve un valor que especifica si los objetos de error son equivalentes.|
|[generic_category](#generic)||
|[message](#message)|Devuelve el nombre del código de error especificado.|
|[name](#name)|Devuelve el nombre de la categoría.|
|[system_category](#system)||

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)|Comprueba la igualdad entre objetos `error_category`.|
|[operator!=](#op_neq)|Comprueba la desigualdad entre objetos `error_category`.|
|[operator<](#op_lt)|Comprueba si el objeto [error_category](../standard-library/error-category-class.md) es menor que el objeto `error_category` pasado para la comparación.|

## <a name="default_error_condition"></a><a name="default_error_condition"></a>default_error_condition

Almacena el valor del código de error para un objeto de condición de error.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parámetros

*_Errval*\
El valor del código de error que se almacenará en la [error_condition](../standard-library/error-condition-class.md).

### <a name="return-value"></a>Valor devuelto

Devuelve `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Observaciones

### <a name="equivalent"></a><a name="equivalent"></a>Equivalent

Devuelve un valor que especifica si los objetos de error son equivalentes.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>Parámetros

*_Errval*\
El valor del código de error que se va a comparar.

*_Cond*\
El objeto [error_condition](../standard-library/error-condition-class.md) que se va a comparar.

*_Code*\
El objeto [error_code](../standard-library/error-code-class.md) que se va a comparar.

#### <a name="return-value"></a>Valor devuelto

**true** si la categoría y el valor son iguales; en caso contrario, **false**.

#### <a name="remarks"></a>Observaciones

La primera función miembro devuelve `*this == _Cond.category() && _Cond.value() == _Errval`.

La segunda función miembro devuelve `*this == _Code.category() && _Code.value() == _Errval`.

### <a name="generic_category"></a><a name="generic"></a>generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a>Mensaje

Devuelve el nombre del código de error especificado.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>Parámetros

\ *Val*
El valor del código de error que se va a describir.

#### <a name="return-value"></a>Valor devuelto

Devuelve un nombre descriptivo del código de error *Val* de la categoría.

#### <a name="remarks"></a>Observaciones

### <a name="name"></a><a name="name"></a>Name

Devuelve el nombre de la categoría.

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>Valor devuelto

Devuelve el nombre de la categoría como una cadena de bytes terminada en un valor nulo.

### <a name="operator"></a><a name="op_as"></a>operador =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a>operador = =

Comprueba la igualdad entre objetos `error_category`.

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
El objeto cuya igualdad se va a comprobar.

#### <a name="return-value"></a>Valor devuelto

**True** si los objetos son iguales; **False** si no lo son.

#### <a name="remarks"></a>Observaciones

Este operador miembro devuelve `this == &right`.

### <a name="operator"></a><a name="op_neq"></a>operador! =

Comprueba la desigualdad entre objetos `error_category`.

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
El objeto cuya desigualdad se va a comprobar.

#### <a name="return-value"></a>Valor devuelto

**true** si el objeto `error_category` no es igual al objeto `error_category` que se pasa a la *derecha*; en caso contrario, **false**.

#### <a name="remarks"></a>Observaciones

El operador miembro devuelve `(!*this == right)`.

### <a name="operatorlt"></a><a name="op_lt"></a> operator&lt;

Comprueba si el objeto [error_category](../standard-library/error-category-class.md) es menor que el objeto `error_category` pasado para la comparación.

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>Parámetros

\ *derecha*
Objeto `error_category` que se va a comparar.

#### <a name="return-value"></a>Valor devuelto

**True** si el objeto `error_category` es menor que el objeto `error_category` pasado para la comparación; en caso contrario, **False**.

#### <a name="remarks"></a>Observaciones

El operador miembro devuelve `this < &right`.

### <a name="system_category"></a><a name="system"></a>system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a>value_type

Tipo que representa el valor del código de error almacenado.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Observaciones

Esta definición de tipo es un sinónimo de **int**.
