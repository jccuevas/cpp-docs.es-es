---
title: Operadores ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcbe04fb057ffc8077f422cd784b5d31691df1e3
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="atl-operators"></a>Operadores ATL
Esta sección contiene los temas de referencia para los operadores globales de ATL.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[operator ==](#operator_eq_eq)|Compara dos `CSid` objetos o `SID` estructuras de igualdad.|  
|[operator !=](#operator_neq)|Compara dos `CSid` objetos o `SID` estructuras no son iguales.|  
|[operador <](#operator_lt)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
|[operator >](#operator_gt)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
|[operator <=](#operator_lt__eq)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor o igual que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
|[operator >=](#operator_gt__eq)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor o igual que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsecurity.h.  
  
##  <a name="operator_eq_eq"></a>  operator ==  
 Compara `CSid` objetos o `SID` igualdad de estructuras (identificador de seguridad).  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera `CSid` objeto o `SID` estructura para comparar.  
  
 `rhs`  
 El segundo `CSid` objeto o `SID` estructura para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si los objetos son iguales, **false** si no son iguales.  
  
##  <a name="operator_neq"></a>  operator !=  
 Compara `CSid` objetos o `SID` desigualdad de estructuras (identificador de seguridad).  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera `CSid` objeto o `SID` estructura para comparar.  
  
 `rhs`  
 El segundo `CSid` objeto o `SID` estructura para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si los objetos no son iguales, **false** si son iguales.  
  
##  <a name="operator_lt"></a>  operador <  
 Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera `CSid` objeto o `SID` estructura para comparar.  
  
 `rhs`  
 El segundo `CSid` objeto o `SID` estructura para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la dirección de la `lhs` objeto es menor que la dirección de la `rhs` objeto, **false** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este operador actúa en la dirección de la `CSid` objeto o `SID` de la estructura y se implementa para ofrecer compatibilidad con clases de colección de la biblioteca estándar de C++.  
  
##  <a name="operator_gt"></a>  operator >  
 Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera `CSid` objeto o `SID` estructura para comparar.  
  
 `rhs`  
 El segundo `CSid` objeto o `SID` estructura para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la dirección de la `lhs` es mayor que la dirección de la `rhs`, **false** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este operador actúa en la dirección de la `CSid` objeto o `SID` de la estructura y se implementa para ofrecer compatibilidad con clases de colección de la biblioteca estándar de C++.  
  
##  <a name="operator_lt__eq"></a>  operador < =  
 Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor o igual que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera `CSid` objeto o `SID` estructura para comparar.  
  
 `rhs`  
 El segundo `CSid` objeto o `SID` estructura para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la dirección de la `lhs` es menor o igual que la dirección de la `rhs`, **false** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este operador actúa en la dirección de la `CSid` objeto o `SID` de la estructura y se implementa para ofrecer compatibilidad con clases de colección de la biblioteca estándar de C++.  
  
##  <a name="operator_gt__eq"></a>  operator >=  
 Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor o igual que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parámetros  
 `lhs`  
 La primera `CSid` objeto o `SID` estructura para comparar.  
  
 `rhs`  
 El segundo `CSid` objeto o `SID` estructura para comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la dirección de la `lhs` es mayor o igual que la dirección de la `rhs`, **false** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este operador actúa en la dirección de la `CSid` objeto o `SID` de la estructura y se implementa para ofrecer compatibilidad con clases de colección de la biblioteca estándar de C++.



