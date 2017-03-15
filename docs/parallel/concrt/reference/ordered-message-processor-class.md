---
title: ordered_message_processor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::ordered_message_processor
dev_langs:
- C++
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 17
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
ms.openlocfilehash: a9653c8eb5f05e56fd7812d334575e62dc101d63
ms.lasthandoff: 02/24/2017

---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor (Clase)
Un `ordered_message_processor` es un `message_processor` que permite a los bloques de mensaje procesar los mensajes en el orden que se recibieron.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class ordered_message_processor : public message_processor<T>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de carga de mensajes administrados por el procesador.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ordered_message_processor (Constructor)](#ctor)|Construye un objeto `ordered_message_processor`.|  
|[~ ordered_message_processor (destructor)](#dtor)|Destruye el objeto `ordered_message_processor`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[async_send (método)](#async_send)|Pone en cola los mensajes e inicia una tarea de procesamiento, si aún no ha hecho de forma asincrónica. (Invalida [message_processor:: async_send](message-processor-class.md#async_send).)|  
|[Initialize (método)](#initialize)|Inicializa el `ordered_message_processor` objeto con el grupo de programación, el programador y la función devolución de llamada apropiada.|  
|[initialize_batched_processing (método)](#initialize_batched_processing)|Inicializar el procesamiento de mensajes por lotes|  
|[sync_send (método)](#sync_send)|Sincrónicamente pone en cola los mensajes e inicia una tarea de procesamiento, si esto no se ha hecho ya. (Invalida [message_processor:: sync_send](message-processor-class.md#sync_send).)|  
|[Wait (método)](#wait)|Una espera de vuelta específica del procesador usada en destructores de bloques de mensajes para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo para finalizar antes de destruir el bloque. (Invalida [message_processor:: wait](message-processor-class.md#wait).)|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[process_incoming_message (método)](#process_incoming_message)|La función de procesamiento que se llama de forma asincrónica. Quita los mensajes de la cola y empieza a procesarlos. (Invalida [message_processor:: process_incoming_message](message-processor-class.md#process_incoming_message).)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [message_processor](message-processor-class.md)  
  
 `ordered_message_processor`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameasyncsenda-asyncsend"></a><a name="async_send"></a>async_send 

 Pone en cola los mensajes e inicia una tarea de procesamiento, si aún no ha hecho de forma asincrónica.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Puntero a un mensaje.  
  
##  <a name="a-nameinitializea-initialize"></a><a name="initialize"></a>inicializar 

 Inicializa el `ordered_message_processor` objeto con el grupo de programación, el programador y la función devolución de llamada apropiada.  
  
```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PScheduler`  
 Un puntero al programador que se utiliza para programar las tareas ligeras.  
  
 `_PScheduleGroup`  
 Un puntero al grupo de programación que se usará para programar las tareas ligeras.  
  
 `_Handler`  
 El functor de controlador que se invoca durante la devolución de llamada.  
  
##  <a name="a-nameinitializebatchedprocessinga-initializebatchedprocessing"></a><a name="initialize_batched_processing"></a>initialize_batched_processing 

 Inicializar el procesamiento de mensajes por lotes  
  
```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Processor`  
 El functor de procesador que se invoca durante la devolución de llamada.  
  
 `_Propagator`  
 El functor propagador que se invoca durante la devolución de llamada.  
  
##  <a name="a-namectora-orderedmessageprocessor"></a><a name="ctor"></a>ordered_message_processor 

 Construye un objeto `ordered_message_processor`.  
  
```
ordered_message_processor();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto `ordered_message_processor` no programará controladores sincrónicos o asincrónicos hasta el `initialize` se llama la función.  
  
##  <a name="a-namedtora-orderedmessageprocessor"></a><a name="dtor"></a>~ ordered_message_processor 

 Destruye el objeto `ordered_message_processor`.  
  
```
virtual ~ordered_message_processor();
```  
  
### <a name="remarks"></a>Comentarios  
 Espera a que todas las operaciones asincrónicas pendientes antes de destruir el procesador.  
  
##  <a name="a-nameprocessincomingmessagea-processincomingmessage"></a><a name="process_incoming_message"></a>process_incoming_message 

 La función de procesamiento que se llama de forma asincrónica. Quita los mensajes de la cola y empieza a procesarlos.  
  
```
virtual void process_incoming_message();
```  
  
##  <a name="a-namesyncsenda-syncsend"></a><a name="sync_send"></a>sync_send 

 Sincrónicamente pone en cola los mensajes e inicia una tarea de procesamiento, si esto no se ha hecho ya.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Puntero a un mensaje.  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>esperar 

 Una espera de vuelta específica del procesador usada en destructores de bloques de mensajes para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo para finalizar antes de destruir el bloque.  
  
```
virtual void wait();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

