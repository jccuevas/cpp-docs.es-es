---
title: Operadores de &lt;system_error&gt;
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876289"
---
# <a name="ltsystem_errorgt-operators"></a>Operadores de &lt;system_error&gt;

## <a name="op_eq_eq"></a>operador = =

Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
El objeto cuya igualdad se va a comprobar.

\ *derecha*
El objeto cuya igualdad se va a comprobar.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos son iguales; **False** si no lo son.

### <a name="remarks"></a>Observaciones

Esta función devuelve `left.category() == right.category() && left.value() == right.value()`.

## <a name="op_neq"></a>operador! =

Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
El objeto cuya desigualdad se va a comprobar.

\ *derecha*
El objeto cuya desigualdad se va a comprobar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto que se pasa a la *izquierda* no es igual que el objeto que se pasa a la *derecha*; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

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

\ *izquierda*
Objeto que se va a comparar.

\ *derecha*
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto que se pasa a la *izquierda* es menor que el objeto que se pasa a la *derecha*; En caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Esta función prueba el orden de error.

## <a name="op_ostream"></a>operador&lt;&lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
