---
title: "Event Handling Principles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces duales, event interfaces"
  - "control de eventos, advising event sources"
  - "control de eventos, dual event interfaces"
  - "control de eventos, implementar"
  - "interfaces, event and event sink"
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event Handling Principles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

hay tres pasos comunes a todo el control de eventos.  Necesitará:  
  
-   Implemente la interfaz de evento en el objeto.  
  
-   Advise el origen de eventos que el objeto desee recibir eventos.  
  
-   Unadvise el origen de eventos cuando el objeto ya no necesita recibir eventos.  
  
 La manera en que se implementará la interfaz de eventos dependerá del tipo.  Una interfaz de eventos puede ser vtable, dual, o dispinterface.  Es responsabilidad del diseñador de origen de eventos para definir la interfaz; decida si va a implementar esta interfaz.  
  
> [!NOTE]
>  Aunque no haya razones técnicas que una interfaz de eventos no puede ser dual, hay buenas razones de diseño para evitar el uso de se dobla.  Sin embargo, esto es una decisión realizada por el diseñador y el implementador del origen de eventos.  Puesto que trabaja desde la perspectiva del evento `sink`, debe tener en cuenta la posibilidad de que puede que no tenga ninguna opción pero implementar una interfaz dual de eventos.  Para obtener más información sobre interfaces duales, vea [interfaces duales y ATL](../atl/dual-interfaces-and-atl.md).  
  
 Muestran el origen de eventos se puede dividir en tres pasos:  
  
-   Vea el objeto de origen para [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Llamada [IConnectionPointContainer:: FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) que pasa el IID de la interfaz de eventos que le interesa.  Si es correcto, esto devolverá la interfaz de [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) en un objeto de punto de conexión.  
  
-   Llame a [IConnectionPoint:: Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) que pasa **IUnknown** de receptor de eventos.  Si es correcto, esto devolverá una cookie de `DWORD` que representa la conexión.  
  
 Una vez que haya registrado correctamente el interés en recibir eventos, los métodos de la interfaz de eventos de objeto se denominados según los eventos desencadenados por el objeto de origen.  Cuando ya no necesite recibir eventos, puede devolver la cookie anclar mediante [IConnectionPoint:: Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608).  Esto rompería la conexión entre el origen y el receptor.  
  
 Asegúrese de no ciclos de referencia al controlar eventos.  
  
## Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)