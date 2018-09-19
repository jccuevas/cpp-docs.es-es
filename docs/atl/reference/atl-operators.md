---
title: Operadores ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0741cd65924a2c968153333aa1a557c31f429d45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039782"
---
# <a name="atl-operators"></a>Operadores ATL

Esta sección contiene los temas de referencia para los operadores globales de ATL.

|Operador|Descripción|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|Compara dos `CSid` objetos o `SID` igualdad de estructuras.|
|[operator !=](#operator_neq)|Compara dos `CSid` objetos o `SID` desigualdad de estructuras.|
|[operador <](#operator_lt)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).|
|[operador >](#operator_gt)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).|
|[operador < =](#operator_lt__eq)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor o igual que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).|
|[operador > =](#operator_gt__eq)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor o igual que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsecurity.h.

##  <a name="operator_eq_eq"></a>  operador ==

Compara `CSid` objetos o `SID` igualdad de estructuras (identificador de seguridad).

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera `CSid` objeto o `SID` estructura para comparar.

*RHS*<br/>
El segundo `CSid` objeto o `SID` estructura para comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son iguales; FALSE si no son iguales.

##  <a name="operator_neq"></a>  operador! =

Compara `CSid` objetos o `SID` desigualdad de estructuras (identificador de seguridad).

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera `CSid` objeto o `SID` estructura para comparar.

*RHS*<br/>
El segundo `CSid` objeto o `SID` estructura para comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos no son iguales y FALSE si son iguales.

##  <a name="operator_lt"></a>  operador <

Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera `CSid` objeto o `SID` estructura para comparar.

*RHS*<br/>
El segundo `CSid` objeto o `SID` estructura para comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de la *lhs* objeto es menor que la dirección de la *rhs* objeto, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Este operador actúa en la dirección de la `CSid` objeto o `SID` estructurar y se implementa para ofrecer compatibilidad con las clases de colección de la biblioteca estándar de C++.

##  <a name="operator_gt"></a>  operador >

Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera `CSid` objeto o `SID` estructura para comparar.

*RHS*<br/>
El segundo `CSid` objeto o `SID` estructura para comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de la *lhs* es mayor que la dirección de la *rhs*, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Este operador actúa en la dirección de la `CSid` objeto o `SID` estructurar y se implementa para ofrecer compatibilidad con las clases de colección de la biblioteca estándar de C++.

##  <a name="operator_lt__eq"></a>  operador < =

Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor o igual que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera `CSid` objeto o `SID` estructura para comparar.

*RHS*<br/>
El segundo `CSid` objeto o `SID` estructura para comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de la *lhs* es menor o igual a la dirección de la *rhs*, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Este operador actúa en la dirección de la `CSid` objeto o `SID` estructurar y se implementa para ofrecer compatibilidad con las clases de colección de la biblioteca estándar de C++.

##  <a name="operator_gt__eq"></a>  operador > =

Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor o igual que el `CSid` objeto o `SID` estructura a la derecha (para compatibilidad de la biblioteca estándar de C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
La primera `CSid` objeto o `SID` estructura para comparar.

*RHS*<br/>
El segundo `CSid` objeto o `SID` estructura para comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la dirección de la *lhs* es mayor o igual a la dirección de la *rhs*, FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Este operador actúa en la dirección de la `CSid` objeto o `SID` estructurar y se implementa para ofrecer compatibilidad con las clases de colección de la biblioteca estándar de C++.

