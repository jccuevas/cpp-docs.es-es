---
title: cancellation_token (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d17505a117c0affd8106afad9004e6ec86602a26
ms.lasthandoff: 03/17/2017

---
# <a name="cancellationtoken-class"></a>cancellation_token (Clase)
La clase `cancellation_token` representa la capacidad para determinar si se ha solicitado la cancelación de alguna operación. Se puede asociar un determinado símbolo con un objeto `task_group`, `structured_task_group` o `task` para proporcionar una cancelación implícita. Este token también puede sondearse para la cancelación o puede hacer que se registre una devolución únicamente si se cancela el objeto `cancellation_token_source` asociado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[cancellation_token](#ctor)||  
|[~ cancellation_token (destructor)](#dtor)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[deregister_callback](#deregister_callback)|Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.|  
|[is_cancelable](#is_cancelable)|Devuelve una indicación de si este token se puede cancelar o no.|  
|[is_canceled](#is_canceled)|Devuelve `true` si el token se ha cancelado.|  
|[none](#none)|Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.|  
|[register_callback](#register_callback)|Registra una función de devolución de llamada con el token. La devolución de llamada se realizará únicamente si se cancela el token. Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `cancellation_token`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** pplcancellation_token.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a>~ cancellation_token 

```
~cancellation_token();
```  
  
##  <a name="ctor"></a>cancellation_token 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
##  <a name="deregister_callback"></a>deregister_callback 

 Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Registration`  
 Objeto `cancellation_token_registration` que se corresponde con la devolución de llamada cuyo registro se va a cancelar. Este símbolo se debe haber devuelto anteriormente desde una llamada al método `register`.  
  
##  <a name="is_cancelable"></a>is_cancelable 

 Devuelve una indicación de si este token se puede cancelar o no.  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Indicación de si este token se puede cancelar o no.  
  
##  <a name="is_canceled"></a>is_canceled 

 Devuelve `true` si el token se ha cancelado.  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor `true` si el token se ha cancelado; de lo contrario, el valor `false`.  
  
##  <a name="none"></a>Ninguno 

 Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Token de cancelación que no puede cancelarse.  
  
##  <a name="operator_neq"></a>operador! = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="operator_eq"></a>operador = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="operator_eq_eq"></a>operador == 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="register_callback"></a>register_callback 

 Registra una función de devolución de llamada con el token. La devolución de llamada se realizará únicamente si se cancela el token. Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Function`  
 Tipo del objeto de función que se volverá a llamar cuando se cancele este objeto `cancellation_token`.  
  
 `_Func`  
 Objeto de función que se volverá a llamar cuando se cancele este objeto `cancellation_token`.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `cancellation_token_registration` que se puede utilizar en el método `deregister` para cancelar el registro de una devolución de llamada previamente registrada y evitar que esta se realice. El método producirá una [invalid_operation](invalid-operation-class.md) excepción si se llama en un `cancellation_token` objeto creado con el [cancellation_token:: None](#none) método.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

