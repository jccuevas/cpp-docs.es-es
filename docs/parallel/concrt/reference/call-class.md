---
title: Clase Call | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 894540410e2768be1cb679b5108fc8c694ca02d3
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="call-class"></a>Clase call
Un bloque de mensajería `call` es un `target_block` con varios orígenes y ordenado, que invoca una función especificada al recibir un mensaje.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de carga de los mensajes propagados a este búfer.  
  
 `_FunctorType`  
 La firma de funciones que este bloque puede aceptar.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Llame a](#ctor)|Sobrecargado. Construye un `call` bloque de mensajería.|  
|[~ call (destructor)](#dtor)|Destruye el `call` bloque de mensajería.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|Ejecuta la función de llamada en los mensajes de entrada.|  
|[process_message](#process_message)|Procesa un mensaje aceptado por este `call` bloque de mensajería.|  
|[propagate_message](#propagate_message)|Un mensaje de forma asincrónica, pasa un `ISource` este bloque `call` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[send_message](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` este bloque `call` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[supports_anonymous_source](#supports_anonymous_source)|Reemplaza el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado. (Invalida [ITarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>Llame a 

 Construye un `call` bloque de mensajería.  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Func`  
 Función que se invocará para cada mensaje aceptado.  
  
 `_Filter`  
 Una función de filtro que determina si se deben aceptar los mensajes que se ofrecen.  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `call`.  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `call`. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 El tipo `_Call_method` es un functor con firma `void (T const &)` que es invocado por este `call` el bloque de mensajería para procesar un mensaje.  
  
 El tipo `filter_method` es un functor con firma `bool (T const &)` que es invocado por este `call` el bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.  
  
##  <a name="dtor"></a>~ llamada 

 Destruye el `call` bloque de mensajería.  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Ejecuta la función de llamada en los mensajes de entrada.  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message 

 Procesa un mensaje aceptado por este `call` bloque de mensajería.  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al mensaje que se administrará.  
  
##  <a name="propagate_message"></a>propagate_message 

 Un mensaje de forma asincrónica, pasa un `ISource` este bloque `call` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="send_message"></a>send_message 

 Un mensaje de forma sincrónica, pasa un `ISource` este bloque `call` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 Reemplaza el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Dado que el bloque no posponga los mensajes que se ofrecen.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [transformer (clase)](transformer-class.md)

