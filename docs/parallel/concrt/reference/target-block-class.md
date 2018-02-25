---
title: target_block (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2827e7bbb9a2c23804d90ccb729e990b84f3a442
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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
 El registro de vínculo que se usará para retener los vínculos de origen.  
  
 `_MessageProcessorType`  
 El tipo de procesador para procesar el mensaje.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`source_iterator`|El tipo de iterador para la `source_link_manager` para este `target_block` objeto.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[target_block](#ctor)|Construye un objeto `target_block`.|  
|[~target_block Destructor](#dtor)|Destruye el objeto `target_block`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagate](#propagate)|Forma asincrónica, pasa un mensaje desde un bloque de origen a este bloque de destino.|  
|[send](#send)|Forma sincrónica, pasa un mensaje desde un bloque de origen a este bloque de destino.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[async_send](#async_send)|Envía de forma asincrónica un mensaje para su procesamiento.|  
|[decline_incoming_messages](#decline_incoming_messages)|Indica al bloque que se deben rechazar los mensajes nuevos.|  
|[enable_batched_processing](#enable_batched_processing)|Permite procesar por lotes de procesamiento para este bloque.|  
|[initialize_target](#initialize_target)|Inicializa el objeto base. En concreto, el `message_processor` debe inicializarse el objeto.|  
|[link_source](#link_source)|Vincula un bloque de origen especificado a este `target_block` objeto.|  
|[process_input_messages](#process_input_messages)|Procesa los mensajes que se reciben como entradas.|  
|[process_message](#process_message)|Cuando se invalida en una clase derivada, procesa un mensaje que fue aceptado por este `target_block` objeto.|  
|[propagate_message](#propagate_message)|Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde una `ISource` bloque a este `target_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[register_filter](#register_filter)|Registra un método de filtro que se invocará en cada mensaje recibido.|  
|[remove_sources](#remove_sources)|Desvincula todos los orígenes después de esperar a que finalicen operaciones de envío asincrónico pendiente.|  
|[send_message](#send_message)|Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje desde una `ISource` bloque a este `target_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[sync_send](#sync_send)|Enviar un mensaje para el procesamiento de forma sincrónica.|  
|[unlink_source](#unlink_source)|Desvincula un bloque de origen especificado desde este `target_block` objeto.|  
|[unlink_sources](#unlink_sources)|Desvincula todos los bloques de origen desde este `target_block` objeto. (Invalida [ITarget:: Unlink_sources](itarget-class.md#unlink_sources).)|  
|[wait_for_async_sends](#wait_for_async_sends)|Espera a que todas las propagaciones asincrónicas que se complete.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="async_send"></a> async_send 

 Envía de forma asincrónica un mensaje para su procesamiento.  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al mensaje que se va a enviar.  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages 

 Indica al bloque que se deben rechazar los mensajes nuevos.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método llama al destructor para asegurarse de que se rechazan los nuevos mensajes mientras la destrucción está en curso.  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing 

 Permite procesar por lotes de procesamiento para este bloque.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a> initialize_target 

 Inicializa el objeto base. En concreto, el `message_processor` debe inicializarse el objeto.  
  
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
  
##  <a name="link_source"></a> link_source 

 Vincula un bloque de origen especificado a este `target_block` objeto.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 Un puntero a la `ISource` bloque que está vinculado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe llamarse directamente en un `target_block` objeto. Bloques deberían estar conectados entre sí mediante el `link_target` método en `ISource` bloques, que invocarán el `link_source` método en el destino correspondiente.  
  
##  <a name="process_input_messages"></a> process_input_messages 

 Procesa los mensajes que se reciben como entradas.  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
  
##  <a name="process_message"></a> process_message 

 Cuando se invalida en una clase derivada, procesa un mensaje que fue aceptado por este `target_block` objeto.  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a> propagar 

 Forma asincrónica, pasa un mensaje desde un bloque de origen a este bloque de destino.  
  
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
 A [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="propagate_message"></a> propagate_message 

 Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde una `ISource` bloque a este `target_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
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
 A [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="register_filter"></a> register_filter 

 Registra un método de filtro que se invocará en cada mensaje recibido.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filter`  
 El método de filtro.  
  
##  <a name="remove_sources"></a> remove_sources 

 Desvincula todos los orígenes después de esperar a que finalicen operaciones de envío asincrónico pendiente.  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>Comentarios  
 Todos los bloques de destino deben llamar a esta rutina para quitar los orígenes en su destructor.  
  
##  <a name="send"></a> Enviar 

 Forma sincrónica, pasa un mensaje desde un bloque de origen a este bloque de destino.  
  
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
 A [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
 Mediante el `send` método fuera de inicio del mensaje y propagar mensajes dentro de una red es peligroso y puede provocar un interbloqueo.  
  
 Cuando `send` devuelve el mensaje ya se ha aceptado y transferido en el bloque de destino, o ha sido rechazada por el destino.  
  
##  <a name="send_message"></a> send_message 

 Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje desde una `ISource` bloque a este `target_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este bloque devuelve `declined` a menos que se reemplaza por una clase derivada.  
  
##  <a name="sync_send"></a> sync_send 

 Enviar un mensaje para el procesamiento de forma sincrónica.  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al mensaje que se va a enviar.  
  
##  <a name="ctor"></a> target_block) 

 Construye un objeto `target_block`.  
  
```
target_block();
```  
  
##  <a name="dtor"></a> ~target_block 

 Destruye el objeto `target_block`.  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a> unlink_source 

 Desvincula un bloque de origen especificado desde este `target_block` objeto.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 Un puntero a la `ISource` bloque que se va a desvincular.  
  
##  <a name="unlink_sources"></a> unlink_sources 

 Desvincula todos los bloques de origen desde este `target_block` objeto.  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a> wait_for_async_sends 

 Espera a que todas las propagaciones asincrónicas que se complete.  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa por destructores de bloque de mensaje para asegurarse de que todas las operaciones asincrónicas han tenido tiempo para finalizar antes de destruir el bloque.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ITarget (clase)](itarget-class.md)
