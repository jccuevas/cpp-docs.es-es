---
title: propagator_block (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
ms.openlocfilehash: a34d127baf13434435c9ab359cf75b7b93c21f6d
ms.lasthandoff: 03/17/2017

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
 `_TargetLinkRegistry`  
 El registro de vínculo que se utilizará para retener los vínculos de destino.  
  
 `_SourceLinkRegistry`  
 El registro de vínculo que se utilizará para retener los vínculos de origen.  
  
 `_MessageProcessorType`  
 El tipo de procesador para procesar el mensaje.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`source_iterator`|El tipo de iterador para la `source_link_manager` para este `propagator_block`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[propagator_block](#ctor)|Construye un objeto `propagator_block`.|  
|[~ propagator_block (destructor)](#dtor)|Destruye un objeto `propagator_block`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[propagar](#propagate)|Forma asincrónica, pasa un mensaje de un bloque de origen a este bloque de destino.|  
|[Enviar](#send)|Inicia sincrónicamente un mensaje a este bloque. Llamado por un `ISource` bloque. Cuando esta función se completa, el mensaje ya se habrá propagado en el bloque.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[decline_incoming_messages](#decline_incoming_messages)|Indica al bloque que se deben rechazar los mensajes nuevos.|  
|[initialize_source_and_target](#initialize_source_and_target)|Inicializa el objeto base. En concreto, la `message_processor` objeto debe inicializarse.|  
|[link_source](#link_source)|Vincula un bloque de origen especificado a este `propagator_block` objeto.|  
|[process_input_messages](#process_input_messages)|Procesar mensajes de entrada. Esto sólo es útil para los bloques propagadores, que se derivan de source_block (reemplaza [source_block:: process_input_messages](source-block-class.md#process_input_messages).)|  
|[propagate_message](#propagate_message)|Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde una `ISource` este bloque `propagator_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[register_filter](#register_filter)|Registra un método de filtro que se invocará en cada mensaje recibido.|  
|[remove_network_links](#remove_network_links)|Quita todo el origen y destino vínculos de red de este `propagator_block` objeto.|  
|[send_message](#send_message)|Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje de un `ISource` este bloque `propagator_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[unlink_source](#unlink_source)|Desvincula un bloque de origen especificado de este `propagator_block` objeto.|  
|[unlink_sources](#unlink_sources)|Desvincula todos los bloques de origen desde este `propagator_block` objeto. (Invalida [ITarget:: Unlink_sources](itarget-class.md#unlink_sources).)|  
  
## <a name="remarks"></a>Comentarios  
 Para evitar la herencia múltiple, el `propagator_block` clase hereda de la `source_block` clase y `ITarget` clase abstracta. La mayoría de la funcionalidad de la `target_block` clase se replica aquí.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 `propagator_block`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="decline_incoming_messages"></a>decline_incoming_messages 

 Indica al bloque que se deben rechazar los mensajes nuevos.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se invoca el destructor para asegurarse de que se rechazan los nuevos mensajes mientras la destrucción está en curso.  
  
##  <a name="initialize_source_and_target"></a>initialize_source_and_target 

 Inicializa el objeto base. En concreto, la `message_processor` objeto debe inicializarse.  
  
```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PScheduler`  
 El programador que se usará para programar tareas.  
  
 `_PScheduleGroup`  
 El grupo de programación que se usará para programar tareas.  
  
##  <a name="link_source"></a>link_source 

 Vincula un bloque de origen especificado a este `propagator_block` objeto.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 Un puntero a la `ISource` bloque que está vinculado.  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Procesar mensajes de entrada. Esto sólo es útil para los bloques propagadores, que se derivan de source_block  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
  
##  <a name="propagate"></a>propagar 

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
 El `propagate` se invoca el método en un bloque de destino por un bloque de origen vinculado. Se pone en cola una tarea asincrónica para controlar el mensaje, si uno no está ya en la cola o ejecutar.  
  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="propagate_message"></a>propagate_message 

 Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje desde una `ISource` este bloque `propagator_block` objeto. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
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
  
##  <a name="ctor"></a>propagator_block 

 Construye un objeto `propagator_block`.  
  
```
propagator_block();
```  
  
##  <a name="dtor"></a>~ propagator_block 

 Destruye un objeto `propagator_block`.  
  
```
virtual ~propagator_block();
```  
  
##  <a name="register_filter"></a>register_filter 

 Registra un método de filtro que se invocará en cada mensaje recibido.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filter`  
 El método de filtro.  
  
##  <a name="remove_network_links"></a>remove_network_links 

 Quita todo el origen y destino vínculos de red de este `propagator_block` objeto.  
  
```
void remove_network_links();
```  
  
##  <a name="send"></a>Enviar 

 Inicia sincrónicamente un mensaje a este bloque. Llamado por un `ISource` bloque. Cuando esta función se completa, el mensaje ya se habrá propagado en el bloque.  
  
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
 Este método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="send_message"></a>send_message 

 Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje de un `ISource` este bloque `propagator_block` objeto. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este bloque devuelve `declined` a menos que se reemplaza por una clase derivada.  
  
##  <a name="unlink_source"></a>unlink_source 

 Desvincula un bloque de origen especificado de este `propagator_block` objeto.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 Un puntero a la `ISource` bloque que se va a desvincular.  
  
##  <a name="unlink_sources"></a>unlink_sources 

 Desvincula todos los bloques de origen desde este `propagator_block` objeto.  
  
```
virtual void unlink_sources();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [source_block (clase)](source-block-class.md)   
 [ITarget (clase)](itarget-class.md)

