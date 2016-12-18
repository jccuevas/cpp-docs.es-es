---
title: "AsyncBase (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncBase (clase)"
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Implementa el equipo de estado asincrónico en tiempo de ejecución de Windows.  
  
## Sintaxis  
  
```  
  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase< TComplete, Details::Nil, resultType >;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase< TComplete, Details::Nil, resultType > : public Microsoft::WRL::Implements< IAsyncInfo >;  
```  
  
#### Parámetros  
 `TComplete`  
 Un controlador de eventos que se llama cuando una operación asincrónica.  
  
 `TProgress`  
 Un controlador de eventos se llama a los informes de una operación asincrónica de ejecución el progreso actual de la operación.  
  
 `resultType`  
 Uno de los valores de enumeración de [AsyncResultType](../windows/asyncresulttype-enumeration.md) .  De forma predeterminada, SingleResult.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AsyncBase::AsyncBase \(Constructor\)](../windows/asyncbase-asyncbase-constructor.md)|Inicializa una instancia de la clase de AsyncBase.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AsyncBase::Cancel \(Método\)](../Topic/AsyncBase::Cancel%20Method.md)|Cancela una operación asincrónica.|  
|[AsyncBase::Close \(Método\)](../windows/asyncbase-close-method.md)|Cierre la operación asincrónica.|  
|[AsyncBase::FireCompletion \(Método\)](../windows/asyncbase-firecompletion-method.md)|Invoca el controlador de eventos de finalización, o restaure el delegado interno de progreso.|  
|[AsyncBase::FireProgress \(Método\)](../windows/asyncbase-fireprogress-method.md)|Invoca el controlador de eventos actual de progreso.|  
|[AsyncBase::get\_ErrorCode \(Método\)](../windows/asyncbase-get-errorcode-method.md)|Recupera el código de error para la operación asincrónica actual.|  
|[AsyncBase::get\_Id \(Método\)](../windows/asyncbase-get-id-method.md)|Recupera el identificador de la operación asincrónica.|  
|[AsyncBase::get\_Status \(Método\)](../Topic/AsyncBase::get_Status%20Method.md)|Recupera un valor que indica el estado de la operación asincrónica.|  
|[AsyncBase::GetOnComplete \(Método\)](../windows/asyncbase-getoncomplete-method.md)|Copie la dirección del controlador de eventos actual de finalización a la variable especificada.|  
|[AsyncBase::GetOnProgress \(Método\)](../windows/asyncbase-getonprogress-method.md)|Copie la dirección del controlador de eventos actual de progreso en la variable especificada.|  
|[AsyncBase::put\_Id \(Método\)](../windows/asyncbase-put-id-method.md)|Establece el identificador de la operación asincrónica.|  
|[AsyncBase::PutOnComplete \(Método\)](../windows/asyncbase-putoncomplete-method.md)|Establece la dirección del controlador de eventos de finalización al valor especificado.|  
|[AsyncBase::PutOnProgress \(Método\)](../windows/asyncbase-putonprogress-method.md)|Establece la dirección del controlador de eventos de progreso al valor especificado.|  
|[AsyncBase::Start \(Método\)](../windows/asyncbase-start-method.md)|Inicia la operación asincrónica.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AsyncBase::CheckValidStateForDelegateCall \(Método\)](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Comprueba si las propiedades del delegado se pueden modificar en el estado asincrónica actual.|  
|[AsyncBase::CheckValidStateForResultsCall \(Método\)](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Comprueba si los resultados de una operación asincrónica se pueden obtener en estado asincrónica actual.|  
|[AsyncBase::ContinueAsyncOperation \(Método\)](../Topic/AsyncBase::ContinueAsyncOperation%20Method.md)|Determina si la operación asincrónica debe continúa o debe detenerse.|  
|[AsyncBase::CurrentStatus \(Método\)](../Topic/AsyncBase::CurrentStatus%20Method.md)|Recupera el estado de la operación asincrónica actual.|  
|[AsyncBase::ErrorCode \(Método\)](../windows/asyncbase-errorcode-method.md)|Recupera el código de error para la operación asincrónica actual.|  
|[AsyncBase::OnCancel \(Método\)](../windows/asyncbase-oncancel-method.md)|Cuando se reemplaza en una clase derivada, cancela una operación asincrónica.|  
|[AsyncBase::OnClose \(Método\)](../windows/asyncbase-onclose-method.md)|Cuando se reemplaza en una clase derivada, cierra una operación asincrónica.|  
|[AsyncBase::OnStart \(Método\)](../windows/asyncbase-onstart-method.md)|Cuando se reemplaza en una clase derivada, comienza una operación asincrónica.|  
|[AsyncBase::TryTransitionToCompleted \(Método\)](../windows/asyncbase-trytransitiontocompleted-method.md)|Indica si la operación asincrónica actual ha finalizado.|  
|[AsyncBase::TryTransitionToError \(Método\)](../windows/asyncbase-trytransitiontoerror-method.md)|Indica si el código de error especificado puede modificar el estado de error interno.|  
  
## Jerarquía de herencia  
 `AsyncBase`  
  
 `AsyncBase`  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)