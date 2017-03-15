---
title: target_block (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::target_block
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 0137e95d0d5015fd2e8d18d85388c16ab25a2e9c
ms.lasthandoff: 02/24/2017

---
# <a name="targetblock-class"></a>target_block (Clase)
La clase `target_block` es una clase base abstracta que proporciona funcionalidad de administración de vínculo básica y comprueba errores solo para bloques de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `_SourceLinkRegistry`  
 El registro de vínculo que se utilizará para retener los vínculos de origen.  
  
 `_MessageProcessorType`  
 El tipo de procesador para procesar el mensaje.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`source_iterator`|El tipo de iterador para la `source_link_manager` para este `target_block` objeto.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[target_block (Constructor)](#ctor)|Construye un objeto `target_block`.|  
|[~ target_block (destructor)](#dtor)|Destruye el objeto `target_block`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[propagate (método)](#propagate)|Forma asincrónica, pasa un mensaje de un bloque de origen a este bloque de destino.|  
|[Send (método)](#send)|Pasa sincrónicamente un mensaje de un bloque de origen a este bloque de destino.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[async_send (método)](#async_send)|Envía de forma asincrónica un mensaje para su procesamiento.|  
|[decline_incoming_messages (método)](#decline_incoming_messages)|Indica al bloque que se deben rechazar los mensajes nuevos.|  
|[enable_batched_processing (método)](#enable_batched_processing)|Permite procesar por lotes de procesamiento para este bloque.|  
|[initialize_target (método)](#initialize_target)|Inicializa el objeto base. En concreto, la `message_processor` objeto debe inicializarse.|  
|[link_source (método)](#link_source)|Vincula un bloque de origen especificado a este `target_block` objeto.|  
|[process_input_messages (método)](#process_input_messages)|Procesa los mensajes que se reciben como entradas.|  
|[process_message (método)](#process_message)|Cuando se invalida en una clase derivada, procesa un mensaje aceptado por este `target_block` objeto.|  
|[propagate_message (método)](#propagate_message)|Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde una `ISource` este bloque `target_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[register_filter (método)](#register_filter)|Registra un método de filtro que se invocará en cada mensaje recibido.|  
|[remove_sources (método)](#remove_sources)|Desvincula todos los orígenes después de esperar a que finalicen operaciones de envío asincrónico pendientes.|  
|[send_message (método)](#send_message)|Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje de un `ISource` este bloque `target_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[sync_send (método)](#sync_send)|Enviar un mensaje para procesar de forma sincrónica.|  
|[unlink_source (método)](#unlink_source)|Desvincula un bloque de origen especificado de este `target_block` objeto.|  
|[unlink_sources (método)](#unlink_sources)|Desvincula todos los bloques de origen desde este `target_block` objeto. (Invalida [ITarget:: Unlink_sources](itarget-class.md#unlink_sources).)|  
|[wait_for_async_sends (método)](#wait_for_async_sends)|Espera a que todas las propagaciones asincrónicas completar.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameasyncsenda-asyncsend"></a><a name="async_send"></a>async_send 

 Envía de forma asincrónica un mensaje para su procesamiento.  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al mensaje que se envían.  
  
##  <a name="a-namedeclineincomingmessagesa-declineincomingmessages"></a><a name="decline_incoming_messages"></a>decline_incoming_messages 

 Indica al bloque que se deben rechazar los mensajes nuevos.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se invoca el destructor para asegurarse de que se rechazan los nuevos mensajes mientras la destrucción está en curso.  
  
##  <a name="a-nameenablebatchedprocessinga-enablebatchedprocessing"></a><a name="enable_batched_processing"></a>enable_batched_processing 

 Permite procesar por lotes de procesamiento para este bloque.  
  
```
void enable_batched_processing();
```  
  
##  <a name="a-nameinitializetargeta-initializetarget"></a><a name="initialize_target"></a>initialize_target 

 Inicializa el objeto base. En concreto, la `message_processor` objeto debe inicializarse.  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PScheduler`  
 El programador que se usará para programar tareas.  
  
 `_PScheduleGroup`  
 El grupo de programación que se usará para programar tareas.  
  
##  <a name="a-namelinksourcea-linksource"></a><a name="link_source"></a>link_source 

 Vincula un bloque de origen especificado a este `target_block` objeto.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 Un puntero a la `ISource` bloque que está vinculado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe llamarse directamente en un `target_block` objeto. Bloques deberían estar conectados entre sí mediante el `link_target` método `ISource` bloques, que invocarán el `link_source` método en el destino correspondiente.  
  
##  <a name="a-nameprocessinputmessagesa-processinputmessages"></a><a name="process_input_messages"></a>process_input_messages 

 Procesa los mensajes que se reciben como entradas.  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
  
##  <a name="a-nameprocessmessagea-processmessage"></a><a name="process_message"></a>process_message 

 Cuando se invalida en una clase derivada, procesa un mensaje aceptado por este `target_block` objeto.  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="a-namepropagatea-propagate"></a><a name="propagate"></a>propagar 

 Forma asincrónica, pasa un mensaje de un bloque de origen a este bloque de destino.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde una `ISource` este bloque `target_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="a-nameregisterfiltera-registerfilter"></a><a name="register_filter"></a>register_filter 

 Registra un método de filtro que se invocará en cada mensaje recibido.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filter`  
 El método de filtro.  
  
##  <a name="a-nameremovesourcesa-removesources"></a><a name="remove_sources"></a>remove_sources 

 Desvincula todos los orígenes después de esperar a que finalicen operaciones de envío asincrónico pendientes.  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>Comentarios  
 Todos los bloques de destino deben llamar a esta rutina para quitar los orígenes en su destructor.  
  
##  <a name="a-namesenda-send"></a><a name="send"></a>Enviar 

 Pasa sincrónicamente un mensaje de un bloque de origen a este bloque de destino.  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
 Mediante el `send` método fuera de inicio del mensaje y propagar mensajes dentro de una red es peligroso y puede provocar un interbloqueo.  
  
 Cuando `send` devuelve el mensaje ya se ha aceptado y transferido en el bloque de destino, o ha sido rechazada por el destino.  
  
##  <a name="a-namesendmessagea-sendmessage"></a><a name="send_message"></a>send_message 

 Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje de un `ISource` este bloque `target_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este bloque devuelve `declined` a menos que se reemplaza por una clase derivada.  
  
##  <a name="a-namesyncsenda-syncsend"></a><a name="sync_send"></a>sync_send 

 Enviar un mensaje para procesar de forma sincrónica.  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al mensaje que se envían.  
  
##  <a name="a-namectora-targetblock"></a><a name="ctor"></a>target_block 

 Construye un objeto `target_block`.  
  
```
target_block();
```  
  
##  <a name="a-namedtora-targetblock"></a><a name="dtor"></a>~ target_block 

 Destruye el objeto `target_block`.  
  
```
virtual ~target_block();
```  
  
##  <a name="a-nameunlinksourcea-unlinksource"></a><a name="unlink_source"></a>unlink_source 

 Desvincula un bloque de origen especificado de este `target_block` objeto.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 Un puntero a la `ISource` bloque que se va a desvincular.  
  
##  <a name="a-nameunlinksourcesa-unlinksources"></a><a name="unlink_sources"></a>unlink_sources 

 Desvincula todos los bloques de origen desde este `target_block` objeto.  
  
```
virtual void unlink_sources();
```  
  
##  <a name="a-namewaitforasyncsendsa-waitforasyncsends"></a><a name="wait_for_async_sends"></a>wait_for_async_sends 

 Espera a que todas las propagaciones asincrónicas completar.  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se utiliza por destructores del bloque de mensaje para asegurarse de que todas las operaciones asincrónicas han tenido tiempo para finalizar antes de destruir el bloque.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ITarget (clase)](itarget-class.md)

