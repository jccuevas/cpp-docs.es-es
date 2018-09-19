---
title: error_category (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
dev_langs:
- C++
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37029491c4a438f44c9f1bb27a9d192c14d1f12
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028234"
---
# <a name="errorcategory-class"></a>error_category (Clase)

Representa la base común abstracta de objetos que describe una categoría de códigos de error.

## <a name="syntax"></a>Sintaxis

```cpp
class error_category;
```

## <a name="remarks"></a>Comentarios

Dos objetos predefinidos implementan `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) y [system_category](../standard-library/system-error-functions.md#system_category).

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[value_type](#value_type)|Tipo que representa el valor del código de error almacenado.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[default_error_condition](#default_error_condition)|Almacena el valor del código de error para un objeto de condición de error.|
|[equivalent](#equivalent)|Devuelve un valor que especifica si los objetos de error son equivalentes.|
|[message](#message)|Devuelve el nombre del código de error especificado.|
|[name](#name)|Devuelve el nombre de la categoría.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator==](#op_eq_eq)|Comprueba la igualdad entre objetos `error_category`.|
|[operator!=](#op_neq)|Comprueba la desigualdad entre objetos `error_category`.|
|[operator<](#op_lt)|Comprueba si el objeto [error_category](../standard-library/error-category-class.md) es menor que el objeto `error_category` pasado para la comparación.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<system_error>

**Espacio de nombres:** std

## <a name="default_error_condition"></a>  error_category::default_error_condition

Almacena el valor del código de error para un objeto de condición de error.

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Errval*|El valor del código de error que se almacenará en la [error_condition](../standard-library/error-condition-class.md).|

### <a name="return-value"></a>Valor devuelto

Devuelve `error_condition(_Errval, *this)`.

### <a name="remarks"></a>Comentarios

## <a name="equivalent"></a>  error_category::equivalent

Devuelve un valor que especifica si los objetos de error son equivalentes.

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Errval*|El valor del código de error que se va a comparar.|
|*_Cond*|El objeto [error_condition](../standard-library/error-condition-class.md) que se va a comparar.|
|*_Fragmentos*|El objeto [error_code](../standard-library/error-code-class.md) que se va a comparar.|

### <a name="return-value"></a>Valor devuelto

**True** si la categoría y valor son iguales; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve `*this == _Cond.category() && _Cond.value() == _Errval`.

La segunda función miembro devuelve `*this == _Code.category() && _Code.value() == _Errval`.

## <a name="message"></a>  error_category::message

Devuelve el nombre del código de error especificado.

```cpp
virtual string message(error_code::value_type val) const = 0;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Val*|El valor del código de error que se va a describir.|

### <a name="return-value"></a>Valor devuelto

Devuelve un nombre descriptivo del código de error *val* para la categoría.

### <a name="remarks"></a>Comentarios

## <a name="name"></a>  error_category::name

Devuelve el nombre de la categoría.

```cpp
virtual const char *name() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el nombre de la categoría como una cadena de bytes terminada en un valor nulo.

### <a name="remarks"></a>Comentarios

## <a name="op_eq_eq"></a>  error_category::operator==

Comprueba la igualdad entre objetos `error_category`.

```cpp
bool operator==(const error_category& right) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*right*|El objeto cuya igualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos son iguales; **False** si no lo son.

### <a name="remarks"></a>Comentarios

Este operador miembro devuelve `this == &right`.

## <a name="op_neq"></a>  error_category::operator!=

Comprueba la desigualdad entre objetos `error_category`.

```cpp
bool operator!=(const error_category& right) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*right*|El objeto cuya desigualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si el `error_category` objeto no es igual que el `error_category` objeto pasado en *derecho*; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

El operador miembro devuelve `(!*this == right)`.

## <a name="op_lt"></a>  error_category::operator&lt;

Comprueba si el objeto [error_category](../standard-library/error-category-class.md) es menor que el objeto `error_category` pasado para la comparación.

```cpp
bool operator<(const error_category& right) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*right*|Objeto `error_category` que se va a comparar.|

### <a name="return-value"></a>Valor devuelto

**True** si el objeto `error_category` es menor que el objeto `error_category` pasado para la comparación; en caso contrario, **False**.

### <a name="remarks"></a>Comentarios

El operador miembro devuelve `this < &right`.

## <a name="value_type"></a>  error_category::value_type

Tipo que representa el valor del código de error almacenado.

```cpp
typedef int value_type;
```

### <a name="remarks"></a>Comentarios

Esta definición de tipo es un sinónimo de **int**.

## <a name="see-also"></a>Vea también

[<system_error>](../standard-library/system-error.md)<br/>
