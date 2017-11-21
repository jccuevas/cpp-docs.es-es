---
title: error_code (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
dev_langs: C++
helpviewer_keywords:
- std::error_code
- std::error_code::value_type
- std::error_code::assign
- std::error_code::category
- std::error_code::clear
- std::error_code::default_error_condition
- std::error_code::message
- 
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7674aeb2a2a1e15ceb38af662f51964884b81ada
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="errorcode-class"></a>error_code (Clase)
Representa los errores de sistema de bajo nivel que son específicos de la implementación.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class error_code;
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de tipo de clase `error_code` almacena un valor de código de error y un puntero a un objeto que representa una [category](../standard-library/error-category-class.md) de códigos de error que describen errores de sistema de bajo nivel notificados.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[error_code](#error_code)|Construye un objeto de tipo `error_code`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[value_type](#value_type)|Tipo que representa el valor del código de error almacenado.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[assign](#assign)|Asigna una categoría y un valor de código de error a un código de error.|  
|[category](#category)|Devuelve la categoría del error.|  
|[clear](#clear)|Borra la categoría y el valor del código de error.|  
|[default_error_condition](#default_error_condition)|Devuelve la condición de error predeterminada.|  
|[message](#message)|Devuelve el nombre del código de error.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator==](#op_eq_eq)|Comprueba la igualdad entre objetos `error_code`.|  
|[operator!=](#op_neq)|Comprueba la desigualdad entre objetos `error_code`.|  
|[operator<](#op_lt)|Comprueba si el objeto `error_code` es menor que el objeto `error_code` pasado para la comparación.|  
|[operator=](#op_eq)|Asigna un nuevo valor de enumeración al objeto `error_code`.|  
|[operator bool](#op_bool)|Convierte una variable de tipo `error_code`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<system_error>  
  
 **Espacio de nombres:** std  
  
##  <a name="assign"></a>  error_code::assign  
 Asigna una categoría y un valor de código de error a un código de error.  
  
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
  
##  <a name="category"></a>  error_code::category  
 Devuelve la categoría del error.  
  
```
const error_category& category() const;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="clear"></a>  error_code::clear  
 Borra la categoría y el valor del código de error.  
  
```
clear();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro almacena un valor de código de error cero y un puntero al objeto [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="default_error_condition"></a>  error_code::default_error_condition  
 Devuelve la condición de error predeterminada.  
  
```
error_condition default_error_condition() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La [error_condition](../standard-library/error-condition-class.md) especificada por [default_error_condition](../standard-library/error-category-class.md#default_error_condition).  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro devuelve `category().default_error_condition(value())`.  
  
##  <a name="error_code"></a>  error_code::error_code  
 Construye un objeto de tipo `error_code`.  
  
```
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`val`|El valor del código de error que se almacenará en la `error_code`.|  
|`_Cat`|La categoría del error que se almacenará en la `error_code`.|  
|`_Errcode`|El valor de enumeración que se va a almacenar en la `error_code`.|  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor almacena un valor de código de error cero y un puntero a la [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
 El segundo constructor almacena `val` como el valor de código de error y un puntero a la [error_category](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8).  
  
 El tercer constructor almacena `(value_type)_Errcode` como el valor de código de error y un puntero a la [generic_category](../standard-library/system-error-functions.md#generic_category).  
  
##  <a name="message"></a>  error_code::message  
 Devuelve el nombre del código de error.  
  
```
string message() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una `string` que representa el nombre del código de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro devuelve `category().message(value())`.  
  
##  <a name="op_eq_eq"></a>  error_code::operator==  
 Comprueba la igualdad entre objetos `error_code`.  
  
```
bool operator==(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto cuya igualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos son iguales; **False** si no lo son.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `category() == right.category() && value == right.value()`.  
  
##  <a name="op_neq"></a>  error_code::operator!=  
 Comprueba la desigualdad entre objetos `error_code`.  
  
```
bool operator!=(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto cuya desigualdad se va a comprobar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto `error_code` no es igual que el objeto `error_code` pasado en `right`. De lo contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `!(*this == right)`.  
  
##  <a name="op_lt"></a>  error_code::operator&lt;  
 Comprueba si el objeto [error_code](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) es menor que el objeto `error_code` pasado para la comparación.  
  
```
bool operator<(const error_code& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|El objeto error_code que se va a comparar.|  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto `error_code` es menor que el objeto `error_code` pasado para la comparación; en caso contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `category() < right.category() || category() == right.category() && value < right.value()`.  
  
##  <a name="op_eq"></a>  error_code::operator=  
 Asigna un nuevo valor de enumeración al objeto [error_code](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31).  
  
```
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type&
 operator=(_Enum _Errcode);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Errcode`|El valor de enumeración que se asignará al objeto `error_code`.|  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto `error_code` al que la función miembro está asignando el nuevo valor de enumeración.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro almacena `(value_type)_Errcode` como el valor de código de error y un puntero a la [generic_category](../standard-library/system-error-functions.md#generic_category). Devuelve `*this`.  
  
##  <a name="op_bool"></a>  error_code::operator bool  
 Convierte una variable de tipo `error_code`.  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor booleano del objeto `error_code`.  
  
### <a name="remarks"></a>Comentarios  
 El operador devuelve un valor que se puede convertir en `true` solo si [value](#value) no es igual a cero. El tipo devuelto puede convertirse solo a `bool`, no a `void *` ni a cualquier otro tipo escalar conocido.  
  
##  <a name="value"></a>  error_code::value  
 Devuelve el valor del código de error almacenado.  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del código de error almacenado de tipo [value_type](#value_type).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="value_type"></a>  error_code::value_type  
 Tipo que representa el valor del código de error almacenado.  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta definición de tipo es un sinónimo de `int`.  
  
## <a name="see-also"></a>Vea también  
 [error_category (Clase)](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)



