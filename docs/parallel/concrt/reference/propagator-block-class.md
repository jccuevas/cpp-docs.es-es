---
title: propagator_block (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8423985b1c6b7497d332e792af2f6bf67a4a0bbe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110294"
---
# <a name="propagatorblock-class"></a>propagator_block (Clase)
La clase `propagator_block` es una clase base abstracta para los bloques de mensaje que son un bloque de origen y de destino. Combina la funcionalidad de las clases `source_block` y `target_block`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
 public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parámetros  
*_TargetLinkRegistry*<br/>
El registro de vínculo que se usará para retener los vínculos de destino.  
  
*_SourceLinkRegistry*<br/>
El registro de vínculo que se usará para retener los vínculos de origen.  
  
*_MessageProcessorType*<br/>
El tipo de procesador para procesar los mensajes.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`source_iterator`|El tipo de iterador para el `source_link_manager` para este `propagator_block`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagator_block](#ctor)|Construye un objeto `propagator_block`.|  
|[~ propagator_block (destructor)](#dtor)|Destruye un objeto `propagator_block`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagar](#propagate)|Pasa de forma asincrónica un mensaje de un bloque de origen a este bloque de destino.|  
|[send](#send)|Inicia sincrónicamente un mensaje a este bloque. Lo llama un `ISource` bloque. Cuando se complete esta función, el mensaje ya se habrá propagado en el bloque.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[decline_incoming_messages](#decline_incoming_messages)|Indica al bloque que se deben rechazar los mensajes nuevos.|  
|[initialize_source_and_target](#initialize_source_and_target)|Inicializa el objeto base. En concreto, el `message_processor` objeto debe inicializarse.|  
|[link_source](#link_source)|Vincula un bloque de origen especificado a esta `propagator_block` objeto.|  
|[process_input_messages](#process_input_messages)|Procesar mensajes de entrada. Esto solo es útil para los bloques propagadores, que se derivan de source_block (invalidaciones [source_block::process_input_messages](source-block-class.md#process_input_messages).)|  
|[propagate_message](#propagate_message)|Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `propagator_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[register_filter](#register_filter)|Registra un método de filtro que se invocará en cada mensaje recibido.|  
|[remove_network_links](#remove_network_links)|Quita todo el origen y destino de vínculos de red de este `propagator_block` objeto.|  
|[send_message](#send_message)|Cuando se invalida en una clase derivada, este método pasa sincrónicamente un mensaje desde un `ISource` bloque a este `propagator_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[unlink_source](#unlink_source)|Desvincula un bloque de origen especificado de este `propagator_block` objeto.|  
|[unlink_sources](#unlink_sources)|Desvincula todos los bloques de código fuente de este `propagator_block` objeto. (Invalida [Unlink_sources](itarget-class.md#unlink_sources).)|  
  
## <a name="remarks"></a>Comentarios  
 Para evitar la herencia múltiple, el `propagator_block` clase hereda de la `source_block` clase y `ITarget` clase abstracta. La mayoría de las funciones en el `target_block` clase se replica aquí.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block)](source-block-class.md)  
  
 `propagator_block`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages 

 Indica al bloque que se deben rechazar los mensajes nuevos.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por el destructor para asegurarse de que se rechazan los mensajes nuevos mientras la destrucción está en curso.  
  
##  <a name="initialize_source_and_target"></a> initialize_source_and_target 

 Inicializa el objeto base. En concreto, el `message_processor` objeto debe inicializarse.  
  
```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
*_PScheduler*<br/>
El programador que se usará para programar tareas.  
  
*_PScheduleGroup*<br/>
El grupo de programación que se usará para programar tareas.  
  
##  <a name="link_source"></a> link_source 

 Vincula un bloque de origen especificado a esta `propagator_block` objeto.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
*_PSource*<br/>
Un puntero a la `ISource` bloque que se van a vincular.  
  
##  <a name="process_input_messages"></a> process_input_messages 

 Procesar mensajes de entrada. Esto solo es útil para los bloques propagadores, que se derivan de source_block  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
*Parámetro _PMessage*<br/>
Un puntero al mensaje que debe procesarse.  
  
##  <a name="propagate"></a> propagar 

 Pasa de forma asincrónica un mensaje de un bloque de origen a este bloque de destino.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.  
  
*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El `propagate` método se invoca en un bloque de destino mediante un bloque de origen vinculado. Se pone en cola una tarea asincrónica para controlar el mensaje, si uno no está ya en la cola o ejecutar.  
  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="propagate_message"></a> propagate_message 

 Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `propagator_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.  
  
*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="ctor"></a> propagator_block) 

 Construye un objeto `propagator_block`.  
  
```
propagator_block();
```  
  
##  <a name="dtor"></a> ~ propagator_block) 

 Destruye un objeto `propagator_block`.  
  
```
virtual ~propagator_block();
```  
  
##  <a name="register_filter"></a> register_filter 

 Registra un método de filtro que se invocará en cada mensaje recibido.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
*_Filtrar*<br/>
El método de filtro.  
  
##  <a name="remove_network_links"></a> remove_network_links 

 Quita todo el origen y destino de vínculos de red de este `propagator_block` objeto.  
  
```
void remove_network_links();
```  
  
##  <a name="send"></a> Enviar 

 Inicia sincrónicamente un mensaje a este bloque. Lo llama un `ISource` bloque. Cuando se complete esta función, el mensaje ya se habrá propagado en el bloque.  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.  
  
*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="send_message"></a> send_message 

 Cuando se invalida en una clase derivada, este método pasa sincrónicamente un mensaje desde un `ISource` bloque a este `propagator_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, se devuelve este bloque `declined` a menos que se reemplaza por una clase derivada.  
  
##  <a name="unlink_source"></a> unlink_source 

 Desvincula un bloque de origen especificado de este `propagator_block` objeto.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
*_PSource*<br/>
Un puntero a la `ISource` bloque que se va a desvincular.  
  
##  <a name="unlink_sources"></a> unlink_sources 

 Desvincula todos los bloques de código fuente de este `propagator_block` objeto.  
  
```
virtual void unlink_sources();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [source_block (clase)](source-block-class.md)   
 [ITarget (clase)](itarget-class.md)
