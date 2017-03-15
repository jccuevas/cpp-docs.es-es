---
title: Event (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::event
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
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
ms.openlocfilehash: abda6512f391b59cb48c8e96a489714ee117ae68
ms.lasthandoff: 02/24/2017

---
# <a name="event-class"></a>event (Clase)
Un evento de reinicio manual que es explícitamente consciente del runtime de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class event;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[~ event (destructor)](#dtor)|Destruye un evento.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Reset (método)](#reset)|Restablece el evento a un estado no señalado.|  
|[establecer (método)](#set)|Señala el evento.|  
|[Wait (método)](#wait)|Espera a que se señale el evento.|  
|[wait_for_multiple (método)](#wait_for_multiple)|Espera a que se señalen varios eventos.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[timeout_infinite (constante)](#timeout_infinite)|Valor que indica que una espera nunca debe agotar el tiempo de espera.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `event`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namectora-event"></a><a name="ctor"></a>evento 

 Construye un nuevo evento.  
  
```
_CRTIMP event();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedtora-event"></a><a name="dtor"></a>~ eventos 

 Destruye un evento.  
  
```
~event();
```  
  
### <a name="remarks"></a>Comentarios  
 Se espera que no haya ningún subproceso esperando en el evento cuando el destructor se ejecuta. Permitir que el evento se destruya con subprocesos que todavía esperan da como resultado un comportamiento no definido.  
  
##  <a name="a-namereseta-reset"></a><a name="reset"></a>Restablecer 

 Restablece el evento a un estado no señalado.  
  
```
void reset();
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>conjunto 

 Señala el evento.  
  
```
void set();
```  
  
### <a name="remarks"></a>Comentarios  
 Señalar el evento puede producir un número arbitrario de contextos que esperan en el evento para que se convierta en ejecutable.  
  
##  <a name="a-nametimeoutinfinitea-timeoutinfinite"></a><a name="timeout_infinite"></a>timeout_infinite 

 Valor que indica que una espera nunca debe agotar el tiempo de espera.  
  
```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>esperar 

 Espera a que se señale el evento.  
  
```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Timeout`  
 Indica el número de milisegundos antes de que se agote el tiempo de espera. El valor `COOPERATIVE_TIMEOUT_INFINITE` significa que no hay tiempo de espera.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se satisfizo la espera, se devuelve el valor `0`; de lo contrario, se devuelve el valor `COOPERATIVE_WAIT_TIMEOUT` para indicar que el tiempo de la espera se agota sin haber señalado el evento.  
  
> [!IMPORTANT]
>  En una aplicación de la [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)], no llame a `wait` en el subproceso ASTA puesto que esta llamada puede bloquear el subproceso actual y puede producir que la aplicación deje de responder.  
  
##  <a name="a-namewaitformultiplea-waitformultiple"></a><a name="wait_for_multiple"></a>wait_for_multiple 

 Espera a que se señalen varios eventos.  
  
```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PPEvents`  
 Matriz de eventos en la que se va a esperar. El número de eventos dentro de la matriz viene indicado por el parámetro `count`.  
  
 `count`  
 El número de eventos dentro de la matriz proporcionado por el parámetro `_PPEvents`.  
  
 `_FWaitAll`  
 Si está establecido en el valor `true`, el parámetro especifica que todos los eventos de la matriz proporcionada en el parámetro `_PPEvents` deben señalarse para satisfacer la espera. Si está establecido en el valor `false`, especifica que cualquier evento de la matriz proporcionada en el parámetro `_PPEvents` que se ha señalado satisfará la espera.  
  
 `_Timeout`  
 Indica el número de milisegundos antes de que se agote el tiempo de espera. El valor `COOPERATIVE_TIMEOUT_INFINITE` significa que no hay tiempo de espera.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se satisfizo la espera, el índice de la matriz proporcionada en el parámetro `_PPEvents` que satisfizo la condición de espera; de lo contrario, el valor `COOPERATIVE_WAIT_TIMEOUT` para indicar que el tiempo de la espera se agota sin satisfacer la condición.  
  
### <a name="remarks"></a>Comentarios  
 Si el parámetro `_FWaitAll` está establecido en el valor `true` para indicar que todos los eventos se deben señalar para satisfacer la espera, el índice que devuelve la función no tiene ninguna importancia especial aparte del hecho de que no es el valor `COOPERATIVE_WAIT_TIMEOUT`.  
  
> [!IMPORTANT]
>  En una aplicación de la [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)], no llame a `wait_for_multiple` en el subproceso ASTA puesto que esta llamada puede bloquear el subproceso actual y puede producir que la aplicación deje de responder.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

