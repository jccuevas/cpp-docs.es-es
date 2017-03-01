---
title: promise (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::promise
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
caps.latest.revision: 15
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ad79ecc3497182a451ef85ea53c8ec5603fdca69
ms.lasthandoff: 02/24/2017

---
# <a name="promise-class"></a>promise (Clase)
Describe un *proveedor asincrónico*.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
class promise;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[promise::promise (Constructor)](#promise__promise_constructor)|Construye un objeto `promise`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[promise::get_future](#promise__get_future_method)|Devuelve un objeto [future](../standard-library/future-class.md) asociado a este compromiso.|  
|[promise::set_exception](#promise__set_exception_method)|Establece de forma atómica el resultado de este compromiso para indicar una excepción.|  
|[promise::set_exception_at_thread_exit](#promise__set_exception_at_thread_exit_method)|Establece de forma atómica el resultado de este compromiso para indicar una excepción y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).|  
|[promise::set_value](#promise__set_value_method)|Establece de forma atómica el resultado de este compromiso para indicar un valor.|  
|[promise::set_value_at_thread_exit](#promise__set_value_at_thread_exit_method)|Establece de forma atómica el resultado de este compromiso para indicar un valor y entrega la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).|  
|[promise::swap](#promise__swap_method)|Intercambia el *estado asincrónico asociado* de este compromiso con el de un objeto promise especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[promise::operator=](#promise__operator_eq)|Asignación del estado compartido de este objeto promise.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `promise`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namepromisegetfuturemethoda--promisegetfuture"></a><a name="promise__get_future_method"></a> promise::get_future  
 Devuelve un objeto [future](../standard-library/future-class.md) que tiene el mismo *estado asincrónico asociado* que este objeto promise.  
  
```
future<Ty> get_future();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto promise está vacío, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un [error_code](../standard-library/error-code-class.md) de `no_state`.  
  
 Si ya se ha llamado a este método para un objeto promise que tiene el mismo estado asincrónico asociado, el método produce un `future_error` que tiene un `error_code` de `future_already_retrieved`.  
  
##  <a name="a-namepromiseoperatoreqa--promiseoperator"></a><a name="promise__operator_eq"></a> promise::operator=  
 Transfiere el *estado asincrónico asociado* de un objeto `promise` especificado.  
  
```
promise& operator=(promise&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Other`  
 Objeto `promise`.  
  
### <a name="return-value"></a>Valor devuelto  
 `*this`  
  
### <a name="remarks"></a>Comentarios  
 Este operador transfiere el estado asincrónico asociado de `Other`. Después de la transferencia, `Other` está *vacío*.  
  
##  <a name="a-namepromisepromiseconstructora--promisepromise-constructor"></a><a name="promise__promise_constructor"></a> promise::promise (Constructor)  
 Construye un objeto `promise`.  
  
```
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Al`  
 Asignador de memoria. Para obtener más información, vea [\<allocators>](../standard-library/allocators-header.md).  
  
 `Other`  
 Objeto `promise`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor crea un objeto `promise` *vacío*.  
  
 El segundo constructor crea un objeto `promise` vacío y usa `Al` para la asignación de memoria.  
  
 El tercer constructor crea un objeto `promise` y transfiere el estado asincrónico asociado de `Other` y deja `Other` vacío.  
  
##  <a name="a-namepromisesetexceptionmethoda--promisesetexception"></a><a name="promise__set_exception_method"></a> promise::set_exception  
 Almacena de forma atómica una excepción como resultado de este objeto `promise` y establece el *estado asincrónico asociado* en *listo*.  
  
```
void set_exception(exception_ptr Exc);
```  
  
### <a name="parameters"></a>Parámetros  
 `Exc`  
 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que este método almacena como el resultado de la excepción.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto `promise` no tiene ningún estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.  
  
 Si ya se ha llamado a `set_exception`, [set_exception_at_thread_exit](#promise__set_exception_at_thread_exit_method), [set_value](#promise__set_value_method) o [set_value_at_thread_exit](#promise__set_value_at_thread_exit_method) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.  
  
 Como resultado de este método, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.  
  
##  <a name="a-namepromisesetexceptionatthreadexitmethoda--promisesetexceptionatthreadexit"></a><a name="promise__set_exception_at_thread_exit_method"></a> promise::set_exception_at_thread_exit  
 Establece de forma atómica el resultado de este `promise` para indicar una excepción, entregando la notificación solo después de que se hayan destruido todos los objetos del subproceso local del subproceso actual (normalmente al salir del subproceso).  
  
```
void set_exception_at_thread_exit(exception_ptr Exc);
```  
  
### <a name="parameters"></a>Parámetros  
 `Exc`  
 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que este método almacena como el resultado de la excepción.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto promise no tiene ningún *estado asincrónico asociado*, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.  
  
 Si ya se ha llamado a [set_exception](#promise__set_exception_method), `set_exception_at_thread_exit`, [set_value](#promise__set_value_method) o [set_value_at_thread_exit](#promise__set_value_at_thread_exit_method) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.  
  
 A diferencia de [set_exception](#promise__set_exception_method), este método no establece el estado asincrónico asociado en listo hasta que no se han destruido todos los objetos locales de subprocesos del subproceso actual. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso actual.  
  
##  <a name="a-namepromisesetvaluemethoda--promisesetvalue"></a><a name="promise__set_value_method"></a> promise::set_value  
 Almacena de forma atómica un valor como resultado de este objeto `promise` y establece el *estado asincrónico asociado* en *listo*.  
  
```
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```  
  
### <a name="parameters"></a>Parámetros  
 `Val`  
 Valor que se va a almacenar como resultado.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto `promise` no tiene ningún estado asincrónico asociado, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.  
  
 Si ya se ha llamado a [set_exception](#promise__set_exception_method), [set_exception_at_thread_exit](#promise__set_exception_at_thread_exit_method), `set_value` o [set_value_at_thread_exit](#promise__set_value_at_thread_exit_method) para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.  
  
 Como resultado de este método, se desbloquean todos los subprocesos bloqueados en el estado asincrónico asociado.  
  
 El primer método también produce cualquier excepción que se produce cuando se copia `Val` en el estado asincrónico asociado. En esta situación, el estado asincrónico asociado no se establece en ready.  
  
 El segundo método también produce cualquier excepción que se produce cuando se mueve `Val` en el estado asincrónico asociado. En esta situación, el estado asincrónico asociado no se establece en ready.  
  
 Para la especialización parcial `promise<Ty&>`, el valor almacenado es una referencia a `Val`.  
  
 Para la especialización `promise<void>`, no existe ningún valor almacenado.  
  
##  <a name="a-namepromisesetvalueatthreadexitmethoda--promisesetvalueatthreadexit"></a><a name="promise__set_value_at_thread_exit_method"></a> promise::set_value_at_thread_exit  
 Almacena de forma atómica un valor como resultado de este objeto `promise`.  
  
```
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```  
  
### <a name="parameters"></a>Parámetros  
 `Val`  
 Valor que se va a almacenar como resultado.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto promise no tiene ningún *estado asincrónico asociado*, este método produce un [future_error](../standard-library/future-error-class.md) que tiene un código de error de `no_state`.  
  
 Si ya se ha llamado a [set_exception](#promise__set_exception_method), [set_exception_at_thread_exit](#promise__set_exception_at_thread_exit_method), [set_value](#promise__set_value_method) o `set_value_at_thread_exit` para un objeto `promise` que tiene el mismo estado asincrónico asociado, este método produce un `future_error` que tiene un código de error de `promise_already_satisfied`.  
  
 A diferencia de `set_value`, el estado asincrónico asociado no se establece hasta que no se han destruido todos los objetos de subproceso local del subproceso actual. Normalmente, los subprocesos que están bloqueados en el estado asincrónico asociado no se desbloquean hasta que no se sale del subproceso actual.  
  
 El primer método también produce cualquier excepción que se produce cuando se copia `Val` en el estado asincrónico asociado.  
  
 El segundo método también produce cualquier excepción que se produce cuando se mueve `Val` en el estado asincrónico asociado.  
  
 Para la especialización parcial `promise<Ty&>`, el valor almacenado es una referencia a `Val`.  
  
 Para la especialización `promise<void>`, no existe ningún valor almacenado.  
  
##  <a name="a-namepromiseswapmethoda--promiseswap"></a><a name="promise__swap_method"></a> promise::swap  
 Intercambia el *estado asincrónico asociado* de este objeto promise por el de un objeto especificado.  
  
```
void swap(promise& Other) noexcept;
```  
  
### <a name="parameters"></a>Parámetros  
 `Other`  
 Objeto `promise`.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)




 


