---
title: cancellation_token_source (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pplcancellation_token/concurrency::cancellation_token_source
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 5c80977656308d3174f4141b131c27fd3c162bbe
ms.lasthandoff: 02/24/2017

---
# <a name="cancellationtokensource-class"></a>cancellation_token_source (Clase)
La clase `cancellation_token_source` representa la capacidad para cancelar una operación que se puede cancelar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class cancellation_token_source;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[cancellation_token_source (Constructor)](#ctor)|Sobrecargado. Construye un nuevo objeto `cancellation_token_source`. El origen se puede usar para marcar la cancelación de alguna operación cancelable.|  
|[~ cancellation_token_source (destructor)](#dtor)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Cancel (método)](#cancel)|Cancela el token. Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.|  
|[create_linked_source (método)](#create_linked_source)|Sobrecargado. Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.|  
|[get_token (método)](#get_token)|Devuelve un token de cancelación asociado a este origen. El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador! = (operador)](#operator_neq)||  
|[operador = (operador)](#operator_eq)||  
|[Operator == (operador)](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `cancellation_token_source`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** pplcancellation_token.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namedtora-cancellationtokensource"></a><a name="dtor"></a>~ cancellation_token_source 

```
~cancellation_token_source();
```  
  
##  <a name="a-namecancela-cancel"></a><a name="cancel"></a>Cancelar 

 Cancela el token. Cualquier objeto `task_group`, `structured_task_group` o `task` que utilice el token se cancelará con esta llamada y producirá una excepción en el siguiente punto de interrupción.  
  
```
void cancel() const;
```  
  
##  <a name="a-namectora-cancellationtokensource"></a><a name="ctor"></a>cancellation_token_source 

 Construye un nuevo objeto `cancellation_token_source`. El origen se puede usar para marcar la cancelación de alguna operación cancelable.  
  
```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
##  <a name="a-namecreatelinkedsourcea-createlinkedsource"></a><a name="create_linked_source"></a>create_linked_source 

 Crea un objeto `cancellation_token_source` que se cancela al cancelar el token proporcionado.  
  
```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Iter`  
 `_Src`  
 Token cuya cancelación provocará la cancelación del origen del token devuelto. Observe que el origen del token devuelto también se puede cancelar independientemente del origen incluido en este parámetro.  
  
 `_Begin`  
 El iterador de biblioteca estándar de C++ correspondiente al inicio del intervalo de tokens para realizar escuchas de cancelación.  
  
 `_End`  
 El iterador de biblioteca estándar de C++ correspondiente con el final del intervalo de tokens para realizar escuchas de cancelación.  
  
### <a name="return-value"></a>Valor devuelto  
 `cancellation_token_source` que se cancela cuando se cancela el token proporcionado por el parámetro `_Src`.  
  
##  <a name="a-namegettokena-gettoken"></a><a name="get_token"></a>get_token 

 Devuelve un token de cancelación asociado a este origen. El token devuelto se puede sondear para la cancelación o puede proporcionar una devolución de llamada únicamente si se produce la cancelación.  
  
```
cancellation_token get_token() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Token de cancelación asociado a este origen.  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>operador! = 

```
bool operator!= (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>operador == 

```
bool operator== (const cancellation_token_source& _Src) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
  
### <a name="return-value"></a>Valor devuelto  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

