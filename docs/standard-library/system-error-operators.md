---
title: Operadores de &lt;system_error&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 974b1294f8ef23936d79e64926595779a9019368
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963698"
---
# <a name="ltsystemerrorgt-operators"></a>Operadores de &lt;system_error&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&lt;](#op_lt)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|El objeto cuya igualdad se va a comprobar.|
|*right*|El objeto cuya igualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si los objetos son iguales; **False** si no lo son.

### <a name="remarks"></a>Comentarios

Esta función devuelve `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a> operator!=

Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.

```cpp
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|El objeto cuya desigualdad se va a comprobar.|
|*right*|El objeto cuya desigualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**True** si el objeto pasado en *izquierdo* no es igual que el objeto pasado en *derecho*; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Esta función devuelve `!(left == right)`.

## <a name="op_lt"></a> operator&lt;

Prueba si un objeto es menor que el objeto pasado para la comparación.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*left*|Objeto que se va a comparar.|
|*right*|Objeto que se va a comparar.|

### <a name="return-value"></a>Valor devuelto

**True** si el objeto pasado en *izquierdo* es menor que el objeto pasado en *derecho*; En caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Esta función prueba el orden de error.

## <a name="see-also"></a>Vea también

[<system_error>](../standard-library/system-error.md)<br/>
