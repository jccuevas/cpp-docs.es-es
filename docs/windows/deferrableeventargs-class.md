---
title: "Clase DeferrableEventArgs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Clase DeferrableEventArgs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla utilizada para los tipos de argumento de evento de los aplazamientos.  
  
## Sintaxis  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### Parámetros  
 `TEventArgsInterface`  
 El tipo de interfaz que declara los argumentos de un evento diferido.  
  
 `TEventArgsClass`  
 La clase que implementa `TEventArgsInterface`.  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Método DeferrableEventArgs::GetDeferral](../windows/deferrableeventargs-getdeferral-method.md)|Obtiene una referencia al objeto [Aplazamiento](http://go.microsoft.com/fwlink/?LinkId=526520) que representa un evento diferido.|  
|[Método DeferrableEventArgs::InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md)|Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.|  
  
## Comentarios  
 Las instancias de esta clase se pasan a los controladores de eventos para eventos diferidos.  Los parámetros de plantilla representan una interfaz que define los detalles de los argumentos de evento de un tipo específico de evento diferido y una clase que implementa esa interfaz.  
  
 La clase aparece como el primer argumento de un controlador de eventos para un evento diferido.  Puede llamar al método [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) para obtener el objeto [Aplazamiento](http://go.microsoft.com/fwlink/?LinkId=526520) desde el que puede obtener toda la información relativa al evento diferido.  Tras completar el control de eventos, debe llamar a Complete en el objeto Aplazamiento.  A continuación, debe llamar a [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) al final del método de controlador de eventos, que garantiza que la finalización de todos los eventos diferidos se comunique correctamente.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)