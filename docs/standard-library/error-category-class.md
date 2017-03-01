---
title: error_category (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::error_category
- system_error/std::error_category
- error_category
- std.error_category
dev_langs:
- C++
helpviewer_keywords:
- error_category class
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 7700ffce8b04f9caad33c08f03f0585c29a43efd
ms.lasthandoff: 02/24/2017

---
# <a name="errorcategory-class"></a>error_category (Clase)
Representa la base común abstracta de objetos que describe una categoría de códigos de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class error_category;
```  
  
## <a name="remarks"></a>Comentarios  
 Dos objetos predefinidos implementan `error_category`: [generic_category](../standard-library/system-error-functions.md#generic_category) y [system_category](../standard-library/system-error-functions.md#system_category).  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[value_type](#error_category__value_type)|Tipo que representa el valor del código de error almacenado.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[default_error_condition](#error_category__default_error_condition)|Almacena el valor del código de error para un objeto de condición de error.|  
|[equivalent](#error_category__equivalent)|Devuelve un valor que especifica si los objetos de error son equivalentes.|  
|[message](#error_category__message)|Devuelve el nombre del código de error especificado.|  
|[name](#error_category__name)|Devuelve el nombre de la categoría.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator==](#error_category__operator_eq_eq)|Comprueba la igualdad entre objetos `error_category`.|  
|[operator!=](#error_category__operator_neq)|Comprueba la desigualdad entre objetos `error_category`.|  
|[operator<](#error_category__operator_lt_)|Comprueba si el objeto [error_category](../standard-library/error-category-class.md) es menor que el objeto `error_category` pasado para la comparación.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<system_error>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameerrorcategorydefaulterrorconditiona--errorcategorydefaulterrorcondition"></a><a name="error_category__default_error_condition"></a>  error_category::default_error_condition  
 Almacena el valor del código de error para un objeto de condición de error.  
  
```
virtual error_condition default_error_condition(int _Errval) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Errval`|El valor del código de error que se almacenará en la [error_condition](../standard-library/error-condition-class.md).|  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `error_condition(_Errval, *this)`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameerrorcategoryequivalenta--errorcategoryequivalent"></a><a name="error_category__equivalent"></a>  error_category::equivalent  
 Devuelve un valor que especifica si los objetos de error son equivalentes.  
  
```
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Errval`|El valor del código de error que se va a comparar.|  
|`_Cond`|El objeto [error_condition](../standard-library/error-condition-class.md) que se va a comparar.|  
|`_Code`|El objeto [error_code](../standard-library/error-code-class.md) que se va a comparar.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la categoría y el valor son iguales; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro devuelve `*this == _Cond.category() && _Cond.value() == _Errval`.  
  
 La segunda función miembro devuelve `*this == _Code.category() && _Code.value() == _Errval`.  
  
##  <a name="a-nameerrorcategorymessagea--errorcategorymessage"></a><a name="error_category__message"></a>  error_category::message  
 Devuelve el nombre del código de error especificado.  
  
```
virtual string message(error_code::value_type val) const = 0;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`val`|El valor del código de error que se va a describir.|  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un nombre descriptivo del código de error `val` para la categoría.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameerrorcategorynamea--errorcategoryname"></a><a name="error_category__name"></a>  error_category::name  
 Devuelve el nombre de la categoría.  
  
```
virtual const char *name() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el nombre de la categoría como una cadena de bytes terminada en un valor nulo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameerrorcategoryoperatoreqeqa--errorcategoryoperator"></a><a name="error_category__operator_eq_eq"></a>  error_category::operator==  
 Comprueba la igualdad entre objetos `error_category`.  
  
```
bool operator==(const error_category& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto cuya igualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos son iguales; **False** si no lo son.  
  
### <a name="remarks"></a>Comentarios  
 Este operador miembro devuelve `this == &right`.  
  
##  <a name="a-nameerrorcategoryoperatorneqa--errorcategoryoperator"></a><a name="error_category__operator_neq"></a>  error_category::operator!=  
 Comprueba la desigualdad entre objetos `error_category`.  
  
```
bool operator!=(const error_category& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto cuya desigualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto `error_category` no es igual que el objeto `error_category` pasado en `right`. De lo contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `(!*this == right)`.  
  
##  <a name="a-nameerrorcategoryoperatorlta--errorcategoryoperatorlt"></a><a name="error_category__operator_lt_"></a>  error_category::operator&lt;  
 Comprueba si el objeto [error_category](../standard-library/error-category-class.md) es menor que el objeto `error_category` pasado para la comparación.  
  
```
bool operator<(const error_category& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|Objeto `error_category` que se va a comparar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto `error_category` es menor que el objeto `error_category` pasado para la comparación; en caso contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `this < &right`.  
  
##  <a name="a-nameerrorcategoryvaluetypea--errorcategoryvaluetype"></a><a name="error_category__value_type"></a>  error_category::value_type  
 Tipo que representa el valor del código de error almacenado.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta definición de tipo es un sinónimo de `int`.  
  
## <a name="see-also"></a>Vea también  
 [<system_error>](../standard-library/system-error.md)




