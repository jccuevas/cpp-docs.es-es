---
title: Clase de mensaje | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
dev_langs:
- C++
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: 21
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
ms.openlocfilehash: c6cc72c1fe9385eabe86194031913b7363d602ff
ms.lasthandoff: 03/17/2017

---
# <a name="message-class"></a>message (Clase)
El sobre del mensaje básico que contiene la carga de datos que se pasa entre bloques de mensajería.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de la carga dentro del mensaje.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[message](#ctor)|Sobrecargado. Construye un objeto `message`.|  
|[~ message (destructor)](#dtor)|Destruye el objeto `message`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[add_ref](#add_ref)|Agrega al recuento de referencias para el `message` objeto. Utiliza bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.|  
|[msg_id](#msg_id)|Devuelve el identificador de la `message` objeto.|  
|[remove_ref](#remove_ref)|Resta el recuento de referencias para el `message` objeto. Utiliza bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[carga](#payload)|La carga de la `message` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `message`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="add_ref"></a>add_ref 

 Agrega al recuento de referencias para el `message` objeto. Utiliza bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.  
  
```
long add_ref();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo valor del recuento de referencias.  
  
##  <a name="ctor"></a>Mensaje 

 Construye un objeto `message`.  
  
```
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```  
  
### <a name="parameters"></a>Parámetros  
 `_P`  
 La carga de este mensaje.  
  
 `_Id`  
 El identificador único de este mensaje.  
  
 `_Msg`  
 Una referencia o un puntero a un `message` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El constructor que toma un puntero a un `message` objeto como argumento, se produce un [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_Msg` es `NULL`.  
  
##  <a name="dtor"></a>~ mensaje 

 Destruye el objeto `message`.  
  
```
virtual ~message();
```  
  
##  <a name="msg_id"></a>msg_id 

 Devuelve el identificador de la `message` objeto.  
  
```
runtime_object_identity msg_id() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `runtime_object_identity` de la `message` objeto.  
  
##  <a name="payload"></a>carga 

 La carga de la `message` objeto.  
  
```
T const payload;
```  
  
##  <a name="remove_ref"></a>remove_ref 

 Resta el recuento de referencias para el `message` objeto. Utiliza bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.  
  
```
long remove_ref();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo valor del recuento de referencias.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

