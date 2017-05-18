---
title: error_condition (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::error_condition
- error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
dev_langs:
- C++
helpviewer_keywords:
- error_condition class
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
caps.latest.revision: 16
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a9171a3f28109f38e3ff3844797e242c669f36c2
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="errorcondition-class"></a>error_condition (Clase)
Representa los códigos de error definidos por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class error_condition;
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de tipo `error_condition` almacena un valor de código de error y un puntero a un objeto que representa una [category](../standard-library/error-category-class.md) de códigos de error que se usan para errores definidos por el usuario notificados.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[error_condition](#error_condition)|Construye un objeto de tipo `error_condition`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[value_type](#value_type)|Tipo que representa el valor del código de error almacenado.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[assign](#assign)|Asigna una categoría y un valor de código de error a una condición de error.|  
|[category](#category)|Devuelve la categoría del error.|  
|[clear](#clear)|Borra la categoría y el valor del código de error.|  
|[message](#message)|Devuelve el nombre del código de error.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator==](#op_eq_eq)|Comprueba la igualdad entre objetos `error_condition`.|  
|[operator!=](#op_neq)|Comprueba la desigualdad entre objetos `error_condition`.|  
|[operator<](#op_lt)|Comprueba si el objeto `error_condition` es menor que el objeto `error_code` pasado para la comparación.|  
|[operator=](#op_eq)|Asigna un nuevo valor de enumeración al objeto `error_condition`.|  
|[operator bool](#op_bool)|Convierte una variable de tipo `error_condition`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<system_error>  
  
 **Espacio de nombres:** std  
  
##  <a name="assign"></a>  error_condition::assign  
 Asigna una categoría y un valor de código de error a una condición de error.  
  
```
void assign(value_type val, const error_category& _Cat);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`val`|El valor del código de error que se almacenará en la `error_code`.|  
|`_Cat`|La categoría del error que se almacenará en el `error_code`.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro almacena `val` como el valor del código de error y un puntero a `_Cat`.  
  
##  <a name="category"></a>  error_condition::category  
 Devuelve la categoría del error.  
  
```
const error_category& category() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la categoría del error almacenada.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="clear"></a>  error_condition::clear  
 Borra la categoría y el valor del código de error.  
  
```
clear();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro almacena un valor de código de error cero y un puntero al objeto [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="error_condition"></a>  error_condition::error_condition  
 Construye un objeto de tipo `error_condition`.  
  
```
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`val`|El valor del código de error que se almacenará en la `error_condition`.|  
|`_Cat`|La categoría del error que se almacenará en la `error_condition`.|  
|`_Errcode`|El valor de enumeración que se va a almacenar en la `error_condition`.|  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor almacena un valor de código de error cero y un puntero a la [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
 El segundo constructor almacena `val` como el valor de código de error y un puntero a la [error_category](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8).  
  
 El tercer constructor almacena `(value_type)_Errcode` como el valor de código de error y un puntero a la [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="message"></a>  error_condition::message  
 Devuelve el nombre del código de error.  
  
```
string message() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una `string` que representa el nombre del código de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro devuelve `category().message(value())`.  
  
##  <a name="op_eq_eq"></a>  error_condition::operator==  
 Comprueba la igualdad entre objetos `error_condition`.  
  
```
bool operator==(const error_condition& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto cuya igualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos son iguales; **False** si no lo son.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `category() == right.category() && value == right.value()`.  
  
##  <a name="op_neq"></a>  error_condition::operator!=  
 Comprueba la desigualdad entre objetos `error_condition`.  
  
```
bool operator!=(const error_condition& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto cuya desigualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto `error_condition` no es igual que el objeto `error_condition` pasado en `right`. De lo contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `!(*this == right)`.  
  
##  <a name="op_lt"></a>  error_condition::operator&lt;  
 Comprueba si el objeto `error_condition` es menor que el objeto `error_code` pasado para la comparación.  
  
```
bool operator<(const error_condition& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|Objeto `error_condition` que se va a comparar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto `error_condition` es menor que el objeto `error_condition` pasado para la comparación; en caso contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `category() < right.category() || category() == right.category() && value < right.value()`.  
  
##  <a name="op_eq"></a>  error_condition::operator=  
 Asigna un nuevo valor de enumeración al objeto `error_condition`.  
  
```
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
 operator=(Enum _Errcode);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Errcode`|El valor de enumeración que se asignará al objeto `error_condition`.|  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto `error_condition` al que la función miembro está asignando el nuevo valor de enumeración.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro almacena `(value_type)error` como el valor de código de error y un puntero a la [generic_category](../standard-library/system-error-functions.md#generic_category). Devuelve `*this`.  
  
##  <a name="op_bool"></a>  error_condition::operator bool  
 Convierte una variable de tipo `error_condition`.  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor booleano del objeto `error_condition`.  
  
### <a name="remarks"></a>Comentarios  
 El operador devuelve un valor que se puede convertir en `true` solo si [value](#value) no es igual a cero. El tipo devuelto puede convertirse solo a `bool`, no a `void *` ni a cualquier otro tipo escalar conocido.  
  
##  <a name="value"></a>  error_condition::value  
 Devuelve el valor del código de error almacenado.  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del código de error almacenado de tipo [value_type](#value_type).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="value_type"></a>  error_condition::value_type  
 Tipo que representa el valor del código de error almacenado.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Comentarios  
 La definición de tipo es un sinónimo de `int`.  
  
## <a name="see-also"></a>Vea también  
 [error_category (Clase)](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)




