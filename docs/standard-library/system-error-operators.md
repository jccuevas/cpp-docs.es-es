---
title: Operadores de &lt;system_error&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 82f7876aca66524ba50b1e01b74437d8a2117976
ms.lasthandoff: 02/24/2017

---
# <a name="ltsystemerrorgt-operators"></a>Operadores de &lt;system_error&gt;
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&lt;](#operator_lt_)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.  
  
```
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|El objeto que se va a probar para comprobar la igualdad.|  
|`right`|El objeto que se va a probar para comprobar la igualdad.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos son iguales; **False** si no lo son.  
  
### <a name="remarks"></a>Comentarios  
 Esta función devuelve `left.category() == right.category() && left.value() == right.value()`.  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.  
  
```
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
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 Prueba si un objeto es menor que el objeto pasado para la comparación.  
  
```
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
 [<system_error>](../standard-library/system-error.md)




