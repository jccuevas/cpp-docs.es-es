---
title: ISource (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::ISource
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
caps.latest.revision: 20
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
ms.openlocfilehash: db3ba296a96b2e77c0ae7d9be3d0a499fe2e7f76
ms.lasthandoff: 02/24/2017

---
# <a name="isource-class"></a>ISource (Clase)
La clase `ISource` es la interfaz para todos los bloques de origen. Los bloques de origen propagan mensajes a los bloques `ITarget`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class ISource;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de la carga dentro de los mensajes generados por el bloque de origen.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`source_type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[~ ISource (destructor)](#dtor)|Destruye el objeto `ISource`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Accept (método)](#accept)|Cuando se invalida en una clase derivada, acepta un mensaje que fue proporcionado por este `ISource` bloque, transfiriendo la propiedad al llamador.|  
|[acquire_ref (método)](#acquire_ref)|Cuando se invalida en una clase derivada, adquiere un recuento de referencias en este `ISource` bloquear, para evitar la eliminación.|  
|[consume (método)](#consume)|Cuando se invalida en una clase derivada, consume un mensaje ofrecido previamente por este `ISource` bloquear y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target (método)](#link_target)|Cuando se invalida en una clase derivada, vincula un bloque de destino a esta `ISource` bloque.|  
|[Release (método)](#release)|Cuando se invalida en una clase derivada, libera una reserva de mensaje correcto anterior.|  
|[release_ref (método)](#release_ref)|Cuando se invalida en una clase derivada, libera un recuento de referencias en este `ISource` bloque.|  
|[Reserve (método)](#reserve)|Cuando se invalida en una clase derivada, reserva un mensaje ofrecido previamente por este `ISource` bloque.|  
|[unlink_target (método)](#unlink_target)|Cuando se invalida en una clase derivada, desvincula un bloque de destino de este `ISource` bloquear si se encuentra vinculado previamente.|  
|[unlink_targets (método)](#unlink_targets)|Cuando se invalida en una clase derivada, desvincula todos los bloques de destino desde este `ISource` bloque.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ISource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameaccepta-accept"></a><a name="accept"></a>Aceptar 

 Cuando se invalida en una clase derivada, acepta un mensaje que fue proporcionado por este `ISource` bloque, transfiriendo la propiedad al llamador.  
  
```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `accept` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 El `accept` un destino llama a método mientras se ofrece un mensaje por este `ISource` bloque. El puntero de mensaje devuelto puede ser diferente de la que se pasa a la `propagate` método de la `ITarget` bloquear, si este origen decide realizar una copia del mensaje.  
  
##  <a name="a-nameacquirerefa-acquireref"></a><a name="acquire_ref"></a>acquire_ref 

 Cuando se invalida en una clase derivada, adquiere un recuento de referencias en este `ISource` bloquear, para evitar la eliminación.  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto vinculado a este origen durante el `link_target` método.  
  
##  <a name="a-nameconsumea-consume"></a><a name="consume"></a>consumir 

 Cuando se invalida en una clase derivada, consume un mensaje ofrecido previamente por este `ISource` bloquear y correctamente reservado por el destino, transfiriendo la propiedad al llamador.  
  
```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de reservado `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `consume` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `consume` método es similar a `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.  
  
##  <a name="a-namedtora-isource"></a><a name="dtor"></a>~ ISource 

 Destruye el objeto `ISource`.  
  
```
virtual ~ISource();
```  
  
##  <a name="a-namelinktargeta-linktarget"></a><a name="link_target"></a>link_target 

 Cuando se invalida en una clase derivada, vincula un bloque de destino a esta `ISource` bloque.  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que se vincula a este `ISource` bloque.  
  
##  <a name="a-namereleasea-release"></a><a name="release"></a>la versión 

 Cuando se invalida en una clase derivada, libera una reserva de mensaje correcto anterior.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de reservado `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `release` (método).  
  
##  <a name="a-namereleaserefa-releaseref"></a><a name="release_ref"></a>release_ref 

 Cuando se invalida en una clase derivada, libera un recuento de referencias en este `ISource` bloque.  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>reservar 

 Cuando se invalida en una clase derivada, reserva un mensaje ofrecido previamente por este `ISource` bloque.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `reserve` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se ha reservado correctamente, `false` en caso contrario. Las reservas pueden fallar por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptó por otro destino, el origen podría denegar reservas etc..  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `reserve`, si se realiza correctamente, debe llamar `consume` o `release` para aceptar o ceder la posesión del mensaje, respectivamente.  
  
##  <a name="a-nameunlinktargeta-unlinktarget"></a><a name="unlink_target"></a>unlink_target 

 Cuando se invalida en una clase derivada, desvincula un bloque de destino de este `ISource` bloquear si se encuentra vinculado previamente.  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que se desvincula de este `ISource` bloquear.  
  
##  <a name="a-nameunlinktargetsa-unlinktargets"></a><a name="unlink_targets"></a>unlink_targets 

 Cuando se invalida en una clase derivada, desvincula todos los bloques de destino desde este `ISource` bloque.  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ITarget (clase)](itarget-class.md)

