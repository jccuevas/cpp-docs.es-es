---
title: Principios (ATL) de control de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6ec61751e16bd67686a983b43c79fea138b3fa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling-principles"></a>Principios de control de eventos
Hay tres pasos comunes a todo el control de eventos. Necesitará:  
  
-   Implemente la interfaz de eventos en el objeto.  
  
-   Notificar al origen de eventos que su objeto quiere recibir eventos.  
  
-   No notificar el origen del evento cuando el objeto ya no se necesita recibir eventos.  
  
 La forma en que se implementa la interfaz de eventos dependerá de su tipo. Una interfaz de eventos puede ser vtable, dual o dispinterface. Resulta al diseñador del origen del evento para definir la interfaz; es que implemente esa interfaz.  
  
> [!NOTE]
>  Aunque no hay ningún razones técnicas que una interfaz de eventos no puede ser dual, hay una serie de motivos de diseño para evitar el uso de duales. Sin embargo, esto es una decisión realizada por el diseñador/implementador del evento *origen*. Puesto que está trabajando desde la perspectiva del evento `sink`, es necesario para permitir la posibilidad de que no puede tener cualquier elección pero para implementar una interfaz de evento dual. Para obtener más información sobre interfaces duales, vea [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md).  
  
 Avisa al origen de eventos puede dividirse en tres pasos:  
  
-   Consultar el objeto de origen para [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Llame a [IConnectionPointContainer:: FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) pasando el IID de la interfaz de eventos que le interese. Si tiene éxito, el valor devuelto será el [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interfaz en un objeto de punto de conexión.  
  
-   Llame a [IConnectionPoint:: Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) pasando el **IUnknown** del receptor de eventos. Si tiene éxito, el valor devuelto será una `DWORD` cookie que representa la conexión.  
  
 Una vez que se han registrado correctamente su interés en recibir eventos, métodos de la interfaz del objeto de evento se llamará según los eventos desencadenados por el objeto de origen. Cuando ya no necesite recibir eventos, puede pasar la cookie hacia el punto de conexión a través de [IConnectionPoint:: Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608). Esto interrumpirá la conexión entre el origen y el receptor.  
  
 Tenga cuidado para evitar referencia ciclos al control de eventos.  
  
## <a name="see-also"></a>Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)

