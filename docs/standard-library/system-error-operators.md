---
title: Operadores de &lt;system_error&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
dev_langs:
- C++
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 19329f90b94edada24c4afe124eed4e4e8443b74
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
|`left`|El objeto cuya igualdad se va a comprobar.|
|`right`|El objeto que se va a probar para comprobar la igualdad.|

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
|`left`|El objeto cuya desigualdad se va a comprobar.|
|`right`|El objeto cuya desigualdad se va a comprobar.|

### <a name="return-value"></a>Valor devuelto

**true** si el objeto pasado en `left` no es igual que el objeto pasado en `right`. De lo contrario, es **false**.

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
|`left`|Objeto que se va a comparar.|
|`right`|Objeto que se va a comparar.|

### <a name="return-value"></a>Valor devuelto

**true** si el objeto pasado en `left` es menor que el objeto pasado en `right`. De lo contrario, es **false**.

### <a name="remarks"></a>Comentarios

Esta función prueba el orden de error.

## <a name="see-also"></a>Vea también

[<system_error>](../standard-library/system-error.md)<br/>
