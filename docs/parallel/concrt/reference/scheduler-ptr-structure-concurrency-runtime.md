---
title: scheduler_ptr (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pplinterface/concurrency::scheduler_ptr
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
caps.latest.revision: 8
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 022b5fafc437a8103fe17967a9a5ea54d5b82a39
ms.lasthandoff: 02/24/2017

---
# <a name="schedulerptr-structure"></a>scheduler_ptr (estructura)
Representa un puntero a un programador. Esta clase existe para permitir la especificación de una duración compartida mediante shared_ptr o simplemente permitir una referencia sin formato mediante un puntero sin formato.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de scheduler_ptr::scheduler_ptr](#ctor)|Sobrecargado. Crea un puntero de programador que va de shared_ptr al programador|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scheduler_ptr::Get (método)](#get)|Devuelve el puntero sin formato al programador|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scheduler_ptr:: operator bool (operador)](#operator_bool)|Prueba si el puntero del programador no es null|  
|[scheduler_ptr:: operator -&gt; (operador)](#operator_ptr)|Se comporta como un puntero|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `scheduler_ptr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** pplinterface.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namegeta--schedulerptrget-method"></a><a name="get"></a>scheduler_ptr::Get (método)  
 Devuelve el puntero sin formato al programador  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameoperatorboola--schedulerptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr:: operator bool   
 Prueba si el puntero del programador no es null  
  
''' operador bool() const;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface () * operator->() const;
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
explícita scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);</scheduler_interface>

scheduler_ptr (de) explícita (_In_opt_ scheduler_interface () * pScheduler);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)

