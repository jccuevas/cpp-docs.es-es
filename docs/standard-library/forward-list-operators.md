---
title: '&lt;forward_list&gt; (Operadores) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a560de0a7587b5552fc663bdd2b44734a66b5f73
ms.lasthandoff: 02/24/2017

---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; (Operadores)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es igual que el objeto de lista de reenvíos del lado derecho.  
  
```
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `forward_list`.|  
|`right`|Objeto de tipo `forward_list`.|  
  
### <a name="remarks"></a>Comentarios  
 Esta función de plantilla sobrecarga `operator==` para comparar dos objetos de clase de plantilla `forward_list`. La función devuelve `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador no es igual que el objeto de lista de reenvíos del lado derecho.  
  
```
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `forward_list`.|  
|`right`|Objeto de tipo `forward_list`.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si las listas no son iguales; **False** si son iguales.  
  
### <a name="remarks"></a>Comentarios  
 Esta función de plantilla devuelve `!(left == right)`.  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es menor que el objeto de lista de reenvíos del lado derecho.  
  
```
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `forward_list`.|  
|`right`|Objeto de tipo `forward_list`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la lista del lado izquierdo del operador es menor pero no igual que la lista del lado derecho del operador. Si no es así, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función de plantilla sobrecarga `operator<` para comparar dos objetos de clase de plantilla `forward_list`. La función devuelve `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es menor o igual que el objeto de lista de reenvíos del lado derecho.  
  
```
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `forward_list`.|  
|`right`|Objeto de tipo `forward_list`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la lista del lado izquierdo del operador es menor o igual que la lista del lado derecho del operador. Si no es así, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función de plantilla devuelve `!(right < left)`.  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es mayor que el objeto de lista de reenvíos del lado derecho.  
  
```
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `forward_list`.|  
|`right`|Objeto de tipo `forward_list`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la lista del lado izquierdo del operador es mayor que la lista del lado derecho del operador. Si no es así, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función de plantilla devuelve `right < left`.  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 Comprueba si el objeto de lista de reenvíos del lado izquierdo del operador es mayor o igual que el objeto de lista de reenvíos del lado derecho.  
  
```
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Objeto de tipo `forward_list`.|  
|`right`|Objeto de tipo `forward_list`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la lista de reenvíos del lado izquierdo del operador es mayor o igual que la lista de reenvíos del lado derecho del operador. Si no es así, `false`.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve `!(left < right)`.  
  
## <a name="see-also"></a>Vea también  
 [<forward_list>](../standard-library/forward-list.md)




