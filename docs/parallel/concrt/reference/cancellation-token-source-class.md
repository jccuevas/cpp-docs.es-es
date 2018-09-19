---
title: cancellation_token_source (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5bda0dd4b756ba9228fac8cc5b0de70b6d71f7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053653"
---
# <a name="cancellationtokensource-class"></a>cancellation_token_source (Clase)
La clase `cancellation_token_source` representa la capacidad para cancelar una operación que se puede cancelar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class cancellation_token_source;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation_token_source](#ctor)|Sobrecargado. Construye un nuevo objeto `cancellation_token_source`. El origen se puede usar para marcar la cancelación de alguna operación cancelable.|  
|[~ cancellation_token_source (destructor)](#dtor)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cancelar](#cancel)|Cancela el token. Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.|  
|[create_linked_source](#create_linked_source)|Sobrecargado. Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.|  
|[get_token](#get_token)|Devuelve un token de cancelación asociado a este origen. El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `cancellation_token_source`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** pplcancellation_token.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~ cancellation_token_source) 

```
~cancellation_token_source();
```  
  
##  <a name="cancel"></a> Cancelar 

 Cancela el token. Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.  
  
```
void cancel() const;
```  
  
##  <a name="ctor"></a> cancellation_token_source) 

 Construye un nuevo objeto `cancellation_token_source`. El origen se puede usar para marcar la cancelación de alguna operación cancelable.  
  
```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
*_Src*<br/>
Objeto que se va a copiar o mover.  
  
##  <a name="create_linked_source"></a> create_linked_source 

 Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.  
  
```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```  
  
### <a name="parameters"></a>Parámetros  
*_Iter*<br/>
Tipo de iterador.

*_Src*<br/>
Token cuya cancelación provocará la cancelación del origen del token devuelto. Observe que el origen del token devuelto también se puede cancelar independientemente del origen incluido en este parámetro.  
  
*_Empezar la*<br/>
El iterador de biblioteca estándar de C++ correspondiente al inicio del intervalo de tokens para escuchar para determinar su cancelación.  
  
*_Finalizar*<br/>
El iterador de biblioteca estándar de C++ correspondiente con el final del intervalo de tokens para escuchar para determinar su cancelación.  
  
### <a name="return-value"></a>Valor devuelto  
 `cancellation_token_source` que se cancela cuando se cancela el token proporcionado por el parámetro `_Src`.  
  
##  <a name="get_token"></a> get_token 

 Devuelve un token de cancelación asociado a este origen. El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.  
  
```
cancellation_token get_token() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Token de cancelación asociado a este origen.  
  
##  <a name="operator_neq"></a> operador! = 

```
bool operator!= (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parámetros  
*_Src*<br/>
Operando.
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="operator_eq"></a> operator= 

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
*_Src*<br/>
Operando.

### <a name="return-value"></a>Valor devuelto  
  
##  <a name="operator_eq_eq"></a> operador == 

```
bool operator== (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parámetros  
*_Src*<br/>
Operando.
  
### <a name="return-value"></a>Valor devuelto  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
