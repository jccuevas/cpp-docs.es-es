---
title: ITarget (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::ITarget
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
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
ms.openlocfilehash: aa9001de9ec35f20cd76f701d6b8acc5de7ffde0
ms.lasthandoff: 02/24/2017

---
# <a name="itarget-class"></a>ITarget (Clase)
La clase `ITarget` es la interfaz para todos los bloques de destino. Los bloques de destinos consumen mensajes ofrecidos por los bloques `ISource`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de la carga dentro de los mensajes aceptados por el bloque de destino.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`filter_method`|La firma de cualquier método usado por el bloque que devuelve un `bool` valor para determinar si se debe aceptar un mensaje proporcionado.|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[~ ITarget (destructor)](#dtor)|Destruye el objeto `ITarget`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[propagate (método)](#propagate)|Cuando se invalida en una clase derivada, forma asincrónica, pasa un mensaje desde un bloque de origen a este bloque de destino.|  
|[Send (método)](#send)|Cuando se invalida en una clase derivada, pasa sincrónicamente un mensaje al bloque de destino.|  
|[supports_anonymous_source (método)](#supports_anonymous_source)|Cuando se invalida en una clase derivada, devuelve true o false, según si el bloque de mensajes acepta mensajes ofrecidos por un origen que no está vinculado a él. Si el método invalidado devuelve `true`, el destino no puede posponer un mensaje proporcionado, tal como requiere el consumo de un mensaje pospuesto en un momento posterior para identificarse en su registro de vínculo de sourse.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[link_source (método)](#link_source)|Cuando se invalida en una clase derivada, vincula un bloque de origen especificado a este `ITarget` bloque.|  
|[unlink_source (método)](#unlink_source)|Cuando se invalida en una clase derivada, desvincula un bloque de origen especificado de este `ITarget` bloquear.|  
|[unlink_sources (método)](#unlink_sources)|Cuando se invalida en una clase derivada, desvincula todos los bloques de origen de este `ITarget` bloquear.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ITarget`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namedtora-itarget"></a><a name="dtor"></a>~ ITarget 

 Destruye el objeto `ITarget`.  
  
```
virtual ~ITarget();
```  
  
##  <a name="a-namelinksourcea-linksource"></a><a name="link_source"></a>link_source 

 Cuando se invalida en una clase derivada, vincula un bloque de origen especificado a este `ITarget` bloque.  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 El `ISource` bloquear esto vinculado `ITarget` bloque.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe llamarse directamente en un `ITarget` bloque. Bloques deberían estar conectados entre sí mediante el `link_target` método `ISource` bloques, que invocarán el `link_source` método en el destino correspondiente.  
  
##  <a name="a-namepropagatea-propagate"></a><a name="propagate"></a>propagar 

 Cuando se invalida en una clase derivada, forma asincrónica, pasa un mensaje desde un bloque de origen a este bloque de destino.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
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
  
##  <a name="a-namesenda-send"></a><a name="send"></a>Enviar 

 Cuando se invalida en una clase derivada, pasa sincrónicamente un mensaje al bloque de destino.  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
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
  
##  <a name="a-namesupportsanonymoussourcea-supportsanonymoussource"></a><a name="supports_anonymous_source"></a>supports_anonymous_source 

 Cuando se invalida en una clase derivada, devuelve true o false, según si el bloque de mensajes acepta mensajes ofrecidos por un origen que no está vinculado a él. Si el método invalidado devuelve `true`, el destino no puede posponer un mensaje proporcionado, tal como requiere el consumo de un mensaje pospuesto en un momento posterior para identificarse en su registro de vínculo de sourse.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el bloque puede aceptar el mensaje de un origen que no está vinculado a él `false` en caso contrario.  
  
##  <a name="a-nameunlinksourcea-unlinksource"></a><a name="unlink_source"></a>unlink_source 

 Cuando se invalida en una clase derivada, desvincula un bloque de origen especificado de este `ITarget` bloquear.  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PSource`  
 El `ISource` bloquear desvincula de este `ITarget` bloquear.  
  
### <a name="remarks"></a>Comentarios  
 Esta función no debe llamarse directamente en un `ITarget` bloque. Los bloques deberían estar desconectados usando la `unlink_target` o `unlink_targets` métodos en `ISource` bloques, que se invocarán la `unlink_source` método en el destino correspondiente.  
  
##  <a name="a-nameunlinksourcesa-unlinksources"></a><a name="unlink_sources"></a>unlink_sources 

 Cuando se invalida en una clase derivada, desvincula todos los bloques de origen de este `ITarget` bloquear.  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ISource (clase)](isource-class.md)

