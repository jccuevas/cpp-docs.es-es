---
title: Operadores ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 87aadf7aacc31ded165a8e1380823cb20e614fb1
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="atl-operators"></a>Operadores ATL
Esta sección contiene los temas de referencia para los operadores globales de ATL.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[operador ==](#operator_eq_eq)|Compara dos `CSid` objetos o `SID` estructuras son iguales.|  
|[operador! =](#operator_neq)|Compara dos `CSid` objetos o `SID` desigualdad de estructuras.|  
|[(operador)](#operator_lt)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
|[operador >](#operator_gt)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
|[(operador)<>](#operator_lt__eq)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es menor o igual que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
|[operador > =](#operator_gt__eq)|Comprueba si el `CSid` objeto o `SID` estructura en el lado izquierdo del operador es mayor o igual que el `CSid` objeto o `SID` estructura a la derecha (para la compatibilidad de la biblioteca estándar de C++).|  
  
 Estos operadores se definen en el archivo atlsecurity.h.  
  
##  <a name="operator_eq_eq"></a>operador ==  
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
  
##  <a name="operator_neq"></a>operador! =  
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
  
##  <a name="operator_lt"></a>(operador)  
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
 Este operador actúa en la dirección de la `CSid` objeto o `SID` estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.  
  
##  <a name="operator_gt"></a>operador >  
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
 Este operador actúa en la dirección de la `CSid` objeto o `SID` estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.  
  
##  <a name="operator_lt__eq"></a>(operador)<=></=>  
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
 Devuelve **true** si la dirección de la `lhs` es menor o igual a la dirección de la `rhs`, **false** en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este operador actúa en la dirección de la `CSid` objeto o `SID` estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.  
  
##  <a name="operator_gt__eq"></a>operador > =  
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
 Este operador actúa en la dirección de la `CSid` objeto o `SID` estructura y se implementa para proporcionar compatibilidad con las clases de colección de la biblioteca estándar de C++.




