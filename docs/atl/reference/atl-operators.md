---
title: Operadores ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: fe5363d3d05123c17e45254898e2210797400022
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168857"
---
# <a name="atl-operators"></a>Operadores ATL

Esta sección contiene los temas de referencia de los operadores globales de ATL.

|Operator|Descripción|
|--------------|-----------------|
|[operador = =](#operator_eq_eq)|Compara dos `CSid` objetos o `SID` estructuras para determinar si son iguales.|
|[operador! =](#operator_neq)|Compara dos `CSid` objetos o `SID` estructuras para determinar si no son iguales.|
|[operador <](#operator_lt)|Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es menor que el objeto `CSid` o `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).|
|[operador >](#operator_gt)|Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es mayor que el objeto `CSid` o `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).|
|[operador <=](#operator_lt__eq)|Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es menor o igual que el objeto o `CSid` `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).|
|[operador >=](#operator_gt__eq)|Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es mayor o igual que el objeto o `CSid` `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).|

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLSecurity. h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>operador = =

Compara los `CSid` objetos o `SID` las estructuras (identificador de seguridad) para determinar si son iguales.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer `CSid` objeto o `SID` estructura que se va a comparar.

*rhs*<br/>
Segundo `CSid` objeto o `SID` estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales, FALSE si no son iguales.

## <a name="operator-"></a><a name="operator_neq"></a>operador! =

Compara los `CSid` objetos o `SID` las estructuras (identificador de seguridad) para determinar si no son iguales.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer `CSid` objeto o `SID` estructura que se va a comparar.

*rhs*<br/>
Segundo `CSid` objeto o `SID` estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos no son iguales, FALSE si son iguales.

## <a name="operator-"></a><a name="operator_lt"></a>operador <

Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es menor que el objeto `CSid` o `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer `CSid` objeto o `SID` estructura que se va a comparar.

*rhs*<br/>
Segundo `CSid` objeto o `SID` estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección del objeto *LHS* es menor que la dirección del objeto *RHS* ; de lo contrario, devuelve false.

### <a name="remarks"></a>Observaciones

Este operador actúa en la dirección del objeto `CSid` o `SID` la estructura, y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.

## <a name="operator-"></a><a name="operator_gt"></a>operador >

Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es mayor que el objeto `CSid` o `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer `CSid` objeto o `SID` estructura que se va a comparar.

*rhs*<br/>
Segundo `CSid` objeto o `SID` estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de *LHS* es mayor que la dirección del *RHS*, de lo contrario, es false.

### <a name="remarks"></a>Observaciones

Este operador actúa en la dirección del objeto `CSid` o `SID` la estructura, y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a>operador <=

Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es menor o igual que el objeto o `CSid` `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer `CSid` objeto o `SID` estructura que se va a comparar.

*rhs*<br/>
Segundo `CSid` objeto o `SID` estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de *LHS* es menor o igual que la dirección del *RHS*, de lo contrario, es false.

### <a name="remarks"></a>Observaciones

Este operador actúa en la dirección del objeto `CSid` o `SID` la estructura, y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a>operador >=

Comprueba si el `CSid` objeto o `SID` la estructura del lado izquierdo del operador es mayor o igual que el objeto o `CSid` `SID` la estructura del lado derecho (para la compatibilidad de la biblioteca estándar de C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer `CSid` objeto o `SID` estructura que se va a comparar.

*rhs*<br/>
Segundo `CSid` objeto o `SID` estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de *LHS* es mayor o igual que la dirección de la *RHS*, de lo contrario, es false.

### <a name="remarks"></a>Observaciones

Este operador actúa en la dirección del objeto `CSid` o `SID` la estructura, y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.
