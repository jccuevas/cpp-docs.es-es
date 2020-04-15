---
title: Operadores ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319237"
---
# <a name="atl-operators"></a>Operadores ATL

Esta sección contiene los temas de referencia para los operadores globales ATL.

|Operator|Descripción|
|--------------|-----------------|
|[operador ?](#operator_eq_eq)|Compara dos `CSid` objetos o `SID` estructuras para la igualdad.|
|[operador !-](#operator_neq)|Compara dos `CSid` objetos o `SID` estructuras para la desigualdad.|
|[operador <](#operator_lt)|Comprueba si `CSid` el `SID` objeto o la estructura en el `CSid` lado `SID` izquierdo del operador es menor que el objeto o la estructura en el lado derecho (para la compatibilidad de la biblioteca estándar C++).|
|[operador >](#operator_gt)|Comprueba si `CSid` el `SID` objeto o la estructura en el `CSid` lado `SID` izquierdo del operador es mayor que el objeto o la estructura en el lado derecho (para la compatibilidad de la biblioteca estándar C++).|
|[<del operador ( operador)](#operator_lt__eq)|Comprueba si `CSid` el `SID` objeto o estructura en el lado izquierdo `CSid` del `SID` operador es menor o igual que el objeto o estructura en el lado derecho (para la compatibilidad con la biblioteca estándar C+).|
|[>del operador ( operador)](#operator_gt__eq)|Comprueba si `CSid` el `SID` objeto o estructura en el lado izquierdo `CSid` del `SID` operador es mayor o igual que el objeto o estructura en el lado derecho (para la compatibilidad con la biblioteca estándar C+).|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>operador ?

Compara `CSid` objetos `SID` o estructuras (identificador de seguridad) para la igualdad.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `CSid` primer `SID` objeto o estructura que se va a comparar.

*rhs*<br/>
El `CSid` segundo `SID` objeto o estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales, FALSE si no son iguales.

## <a name="operator-"></a><a name="operator_neq"></a>operador !-

Compara `CSid` objetos `SID` o estructuras (identificador de seguridad) para la desigualdad.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `CSid` primer `SID` objeto o estructura que se va a comparar.

*rhs*<br/>
El `CSid` segundo `SID` objeto o estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos no son iguales, FALSE si son iguales.

## <a name="operator-"></a><a name="operator_lt"></a>< operador

Comprueba si `CSid` el `SID` objeto o la estructura en el `CSid` lado `SID` izquierdo del operador es menor que el objeto o la estructura en el lado derecho (para la compatibilidad de la biblioteca estándar C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `CSid` primer `SID` objeto o estructura que se va a comparar.

*rhs*<br/>
El `CSid` segundo `SID` objeto o estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección del objeto *lhs* es menor que la dirección del objeto *rhs,* FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Este operador actúa en `CSid` la `SID` dirección del objeto o estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.

## <a name="operator-"></a><a name="operator_gt"></a>> operador

Comprueba si `CSid` el `SID` objeto o la estructura en el `CSid` lado `SID` izquierdo del operador es mayor que el objeto o la estructura en el lado derecho (para la compatibilidad de la biblioteca estándar C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `CSid` primer `SID` objeto o estructura que se va a comparar.

*rhs*<br/>
El `CSid` segundo `SID` objeto o estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de *lhs* es mayor que la dirección de *rhs*, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Este operador actúa en `CSid` la `SID` dirección del objeto o estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a><del operador ( operador)

Comprueba si `CSid` el `SID` objeto o estructura en el lado izquierdo `CSid` del `SID` operador es menor o igual que el objeto o estructura en el lado derecho (para la compatibilidad con la biblioteca estándar C+).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `CSid` primer `SID` objeto o estructura que se va a comparar.

*rhs*<br/>
El `CSid` segundo `SID` objeto o estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de *lhs* es menor o igual que la dirección de *rhs*, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Este operador actúa en `CSid` la `SID` dirección del objeto o estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a>>del operador ( operador)

Comprueba si `CSid` el `SID` objeto o estructura en el lado izquierdo `CSid` del `SID` operador es mayor o igual que el objeto o estructura en el lado derecho (para la compatibilidad con la biblioteca estándar C+).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El `CSid` primer `SID` objeto o estructura que se va a comparar.

*rhs*<br/>
El `CSid` segundo `SID` objeto o estructura que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de *lhs* es mayor o igual que la dirección de *rhs*, FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Este operador actúa en `CSid` la `SID` dirección del objeto o estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.
