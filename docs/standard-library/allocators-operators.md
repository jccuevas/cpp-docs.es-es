---
title: '&lt;allocators&gt; (operadores) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 0a2da6c72e8900c0cea86c30c6b8511e6b256ff9
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; (operadores)
|||  
|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 Comprueba la desigualdad entre los objetos de asignador de una clase especificada.  
  
```
template <class Type, class Sync>  
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|  
|`right`|Uno de los objetos de asignador cuya desigualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos de asignador no son iguales y **False** si son iguales.  
  
### <a name="remarks"></a>Comentarios  
 El operador de la plantilla devuelve `!(left == right)`.  
  
##  <a name="op_eq_eq"></a>  operator==  
 Comprueba la igualdad entre los objetos de asignador de una clase especificada.  
  
```
template <class Type, class Sync>  
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`left`|Uno de los objetos de asignador cuya igualdad se va a comprobar.|  
|`right`|Uno de los objetos de asignador cuya igualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos de asignador son iguales y **False** si no lo son.  
  
### <a name="remarks"></a>Comentarios  
 Este operador de la plantilla devuelve `left.equals(right)`.  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




