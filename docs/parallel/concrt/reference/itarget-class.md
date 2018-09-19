---
title: ITarget (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dff803a33a35ad9ca30e0a49b6ef09155e4ec26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020347"
---
# <a name="itarget-class"></a>ITarget (Clase)
La clase `ITarget` es la interfaz para todos los bloques de destino. Los bloques de destinos consumen mensajes ofrecidos por los bloques `ISource`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>Parámetros  
*T*<br/>
El tipo de datos de la carga dentro de los mensajes aceptados por el bloque de destino.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`filter_method`|La firma de cualquier método usado por el bloque que devuelve un `bool` valor para determinar si se debe aceptar un mensaje proporcionado.|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[~ ITarget (destructor)](#dtor)|Destruye el objeto `ITarget`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagar](#propagate)|Cuando se invalida en una clase derivada, asincrónicamente pasa un mensaje desde un bloque de origen a este bloque de destino.|  
|[send](#send)|Cuando se invalida en una clase derivada, pasa sincrónicamente un mensaje al bloque de destino.|  
|[supports_anonymous_source](#supports_anonymous_source)|Cuando se invalida en una clase derivada, devuelve true o false dependiendo de si el bloque de mensajes acepta mensajes ofrecidos por un origen que no está vinculado a él. Si el método invalidado devuelve `true`, el destino no puede posponer un mensaje ofrecido, ya que el consumo de un mensaje pospuesto en un momento posterior requiere el origen pueda identificarse en su registro de vínculo sourse.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[link_source](#link_source)|Cuando se invalida en una clase derivada, vincula un bloque de origen especificado a esta `ITarget` bloque.|  
|[unlink_source](#unlink_source)|Cuando se invalida en una clase derivada, desvincula un bloque de origen especificado de este `ITarget` bloque.|  
|[unlink_sources](#unlink_sources)|Cuando se invalida en una clase derivada, desvincula todos los bloques de código fuente de este `ITarget` bloque.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ITarget`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~ ITarget 

 Destruye el objeto `ITarget`.  
  
```
virtual ~ITarget();
```  
  
##  <a name="link_source"></a> link_source 

 Cuando se invalida en una clase derivada, vincula un bloque de origen especificado a esta `ITarget` bloque.  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*_PSource*<br/>
El `ISource` bloquear que se vinculan a esta `ITarget` bloque.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe llamarse directamente en un `ITarget` bloque. Bloques deberían estar conectados entre sí mediante el `link_target` método `ISource` bloques, que invocarán el `link_source` método en el destino correspondiente.  
  
##  <a name="propagate"></a> propagar 

 Cuando se invalida en una clase derivada, asincrónicamente pasa un mensaje desde un bloque de origen a este bloque de destino.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.  
  
*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
##  <a name="send"></a> Enviar 

 Cuando se invalida en una clase derivada, pasa sincrónicamente un mensaje al bloque de destino.  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.  
  
*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el `_PMessage` o `_PSource` parámetro es `NULL`.  
  
 Mediante el `send` método fuera de inicio del mensaje y propagar los mensajes dentro de una red es peligroso y puede provocar un interbloqueo.  
  
 Cuando `send` devuelve el mensaje ya se ha aceptado y transferido en el bloque de destino, o se ha rechazado por el destino.  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source 

 Cuando se invalida en una clase derivada, devuelve true o false dependiendo de si el bloque de mensajes acepta mensajes ofrecidos por un origen que no está vinculado a él. Si el método invalidado devuelve `true`, el destino no puede posponer un mensaje ofrecido, ya que el consumo de un mensaje pospuesto en un momento posterior requiere el origen pueda identificarse en su registro de vínculo sourse.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el bloque puede aceptar el mensaje de un origen que no está vinculado a él `false` en caso contrario.  
  
##  <a name="unlink_source"></a> unlink_source 

 Cuando se invalida en una clase derivada, desvincula un bloque de origen especificado de este `ITarget` bloque.  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
*_PSource*<br/>
El `ISource` bloquear desvincula de esto `ITarget` bloque.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe llamarse directamente en un `ITarget` bloque. Bloques deberían estar desconectados usando el `unlink_target` o `unlink_targets` métodos en `ISource` bloques, que invocarán el `unlink_source` método en el destino correspondiente.  
  
##  <a name="unlink_sources"></a> unlink_sources 

 Cuando se invalida en una clase derivada, desvincula todos los bloques de código fuente de este `ITarget` bloque.  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ISource (clase)](isource-class.md)
