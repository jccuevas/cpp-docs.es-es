---
title: task_continuation_context (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
dev_langs:
- C++
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 8afd599e5ee489500d7f8c498d03c91ace6b99ed
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context (Clase)
La clase `task_continuation_context` permite especificar dónde se desea que se ejecute una continuación. Solo es de utilidad utilizar esta clase desde una aplicación de la Tienda Windows. Para las aplicaciones que no sean de la Tienda Windows, el contexto de ejecución de la continuación de la tarea determina el runtime y no se puede configurar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class task_continuation_context : public details::_ContextCallback;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[get_current_winrt_context](#get_current_winrt_context)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto del subproceso actual winrt.|  
|[use_arbitrary](#use_arbitrary)|Crea un contexto de continuación de la tarea que permite elegir el contexto de ejecución para una continuación en el runtime.|  
|[use_current](#use_current)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.|  
|[use_default](#use_default)|Crea el contexto de continuación de tarea predeterminado.|  
|[use_synchronous_execution](#use_synchronous_execution)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución sincrónica.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  

## <a name="get_current_winrt_context"></a>get_current_winrt_context
 Devuelve un objeto de contexto de continuación de tarea que representa el contexto del subproceso actual WinRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static task_continuation_context get_current_winrt_context();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El contexto del subproceso actual en tiempo de ejecución de Windows. Devuelve un task_continuation_context vacía si se llama desde un contexto en tiempo de ejecución que no sean de Windows.  
  
## <a name="remarks"></a>Comentarios  
 El `get_current_winrt_context` método captura el contexto del subproceso del llamador en tiempo de ejecución de Windows. Devuelve un contexto vacío para los llamadores en tiempo de ejecución que no sean de Windows.  
  
 El valor devuelto por `get_current_winrt_context` puede utilizarse para indicar al tiempo de ejecución que debe ejecutarse la continuación en el modelo de apartamento del contexto capturado (STA vs MTA), independientemente de si la tarea antecedente es reconoce el apartamento. Un apartamento compatible con la tarea es una tarea que desencapsula un tiempo de ejecución de Windows `IAsyncInfo` interfaz o una tarea que desciende de dicha tarea.  
  
 Este método es similar a la `use_current` (método), pero también está disponible para código nativo de C++ sin C + + / compatibilidad con extensiones CX. Está destinado a usuarios avanzados utilizando escribir C + + / código de biblioteca independiente CX nativo y los llamadores en tiempo de ejecución de Windows. A menos que se necesita esta funcionalidad, se recomienda la `use_current` método, que sólo está disponible para C + + clientes CX.  
  
  
##  <a name="use_arbitrary"></a>use_arbitrary 

 Crea un contexto de continuación de la tarea que permite elegir el contexto de ejecución para una continuación en el runtime.  
  
```
static task_continuation_context use_arbitrary();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un contexto de continuación de tarea que representa una ubicación arbitraria.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se utiliza en este contexto de continuación de la continuación se ejecutará en un contexto que el runtime elige incluso si la tarea antecedente es reconoce el apartamento.  
  
 `use_arbitrary`puede utilizarse para desactivar el comportamiento predeterminado de una continuación de una tarea consciente de apartamento creada en STA.  
  
 Este método solo está disponible para aplicaciones de la tienda de Windows.  
  
##  <a name="use_current"></a>use_current 

 Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.  
  
```
static task_continuation_context use_current();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Contexto de ejecución actual.  
  
### <a name="remarks"></a>Comentarios  
 Este método captura el contexto del llamador en tiempo de ejecución de Windows para que las continuaciones se pueden ejecutar en el contenedor secundario.  
  
 El valor devuelto por `use_current` puede utilizarse para indicar al tiempo de ejecución que debe ejecutarse la continuación en el contexto capturado (STA vs MTA) independientemente de si es o no la tarea antecedente reconoce el apartamento. Un apartamento compatible con la tarea es una tarea que desencapsula un tiempo de ejecución de Windows `IAsyncInfo` interfaz o una tarea que desciende de dicha tarea.  
  
 Este método solo está disponible para aplicaciones de la tienda de Windows.  
  
##  <a name="use_default"></a>use_default 

 Crea el contexto de continuación de tarea predeterminado.  
  
```
static task_continuation_context use_default();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El contexto de continuación de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza el contexto predeterminado si no especifica un contexto de continuación al llamar a la `then` (método). En aplicaciones de Windows para Windows 7 y, a continuación, así como aplicaciones de escritorio en Windows 8 y versiones posteriores, el tiempo de ejecución determina donde se ejecutarán las continuaciones de tareas. Sin embargo, en una aplicación de tienda Windows, el contexto de continuación predeterminado para una continuación en una tarea consciente de apartamento es el contenedor donde `then` se invoca.  
  
 Un apartamento compatible con la tarea es una tarea que desencapsula un tiempo de ejecución de Windows `IAsyncInfo` interfaz o una tarea que desciende de dicha tarea. Por lo tanto, si programa una continuación de una tarea consciente de apartamento en un STA de Windows en tiempo de ejecución, la continuación se ejecutará en ese STA.  
  
 Una continuación en una tarea consciente del apartamento no se ejecutará en un contexto que se elige el tiempo de ejecución.  

## <a name="use_synchronous_execution"></a>task_continuation_context::use_synchronous_execution  
Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución sincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static task_continuation_context use_synchronous_execution();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El contexto de ejecución sincrónica.  
  
## <a name="remarks"></a>Comentarios  
 El `use_synchronous_execution` método hace que la tarea de continuación para ejecutar sincrónicamente en el contexto, provocando la finalización de la tarea anterior.  
  
 Si la tarea anterior se ha completado cuando se adjunta la continuación, la continuación se ejecuta de forma sincrónica en el contexto que se asocia la continuación.  
  
 
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

