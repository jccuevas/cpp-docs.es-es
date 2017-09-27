---
title: 'Controles ActiveX MFC: Eventos | Documentos de Microsoft'
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
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
caps.latest.revision: 10
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
ms.translationtype: HT
ms.sourcegitcommit: 3903be230f130aeaeb1953faf73a0c8af4c3492f
ms.openlocfilehash: f4e6cfc21a12288a53eca391eccb86bb4ea3ff55
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="mfc-activex-controls-events"></a>Controles ActiveX MFC: Eventos
Controles ActiveX utilizan eventos para notificar a un contenedor que ha sucedido algo al control. Algunos ejemplos de eventos son los clics en el control, los datos introducidos mediante el teclado y cambios en el estado del control. Cuando se producen estas acciones, el control desencadena un evento para avisar al contenedor.  
  
 Eventos también se denominan mensajes.  
  
 MFC admite dos tipos de eventos: estándar y personalizados. Eventos estándar son aquellos eventos que la clase [COleControl](../mfc/reference/colecontrol-class.md) controla automáticamente. Para obtener una lista completa de eventos estándar, vea el artículo [controles ActiveX de MFC: agregar eventos estándar](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Eventos personalizados permiten un control de la capacidad notificar al contenedor cuando se produce una acción específica en ese control. Algunos ejemplos serían un cambio en el estado interno de un control o la recepción de un determinado mensaje de ventana.  
  
 Para que el control de eventos se activan correctamente, la clase del control debe asignar cada evento del control a una función miembro que se debe llamar cuando se produce el evento relacionado. Este mecanismo de asignación (denominado mapa de eventos) centraliza la información sobre el evento y permite a Visual Studio fácilmente tener acceso y manipular los eventos del control. Este mapa de eventos se declara mediante la siguiente macro, que se encuentra en el encabezado (. (H) del archivo de la declaración de clase de control:  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]  
  
 Después de que se ha declarado el mapa de eventos, debe definirse en el archivo de implementación (. Archivo CPP). Las siguientes líneas de código definen el mapa de eventos, lo que permite al control activar eventos específicos:  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]  
  
 Si utiliza al Asistente para controles de ActiveX de MFC para crear el proyecto, agrega automáticamente las siguientes líneas. Si no utiliza al Asistente para controles de ActiveX de MFC, debe agregar manualmente estas líneas.  
  
 Con la vista de clases, puede agregar eventos estándar admitidos por la clase `COleControl` o eventos personalizados que defina. Para cada nuevo evento, vista de clases agrega automáticamente la entrada adecuada para el mapa de eventos del control y el control. Este archivo IDL.  
  
 Dos artículos describen los eventos en detalle:  
  
-   [Controles ActiveX MFC: Agregar eventos estándar](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Controles ActiveX MFC: Agregar eventos personalizados](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX de MFC: métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl (clase)](../mfc/reference/colecontrol-class.md)

