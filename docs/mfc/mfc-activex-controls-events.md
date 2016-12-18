---
title: "Controles ActiveX MFC: Eventos | Microsoft Docs"
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
  - "COleControl (clase), control de eventos"
  - "eventos contenedores"
  - "eventos personalizados, agregar a controles ActiveX"
  - "eventos [C++], controles ActiveX"
  - "eventos [C++], asignar"
  - "asignaciones, eventos"
  - "controles ActiveX en MFC, eventos"
  - "notificaciones [C++], notificar contenedores de eventos"
  - "eventos OLE"
  - "eventos estándar"
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Eventos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles ActiveX utilizan eventos para notificar a un contenedor que algo ha ocurrido al control.  Los ejemplos comunes de inclusión de eventos haga clic en el control, los datos especificados mediante el teclado, y cambios en el estado de control.  Cuando estas acciones aparecen, el control desencadena un evento para avisar al contenedor.  
  
 Los eventos también se denominan mensajes.  
  
 MFC admite dos tipos de eventos: acción y personalizado.  Eventos comunes son los eventos que la clase [COleControl](../mfc/reference/colecontrol-class.md) controla automáticamente.  Para obtener una lista completa de los eventos comunes, vea el artículo [Controles ActiveX de MFC: Agregar eventos comunes](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md).  Los eventos personalizados permiten a control la capacidad de notificar el contenedor cuando un concreto de acción a ese control aparece.  Algunos ejemplos serían un cambio en el estado interno de un control o un mensaje de un mensaje de la ventana.  
  
 Para que el control desencadena eventos correctamente, la clase control debe asignar cada evento del control a una función miembro que debe llamar cuando el evento relacionado aparece.  Este mecanismo de asignación \(denominado evento asignado\) centraliza la información sobre el evento y permite que Visual Studio tener acceso fácilmente y manipular a los eventos de control.  Este mapa de evento es declarado por la siguiente macro, ubicada en el encabezado \(. H\) archivo de la declaración de clase de control:  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/CPP/mfc-activex-controls-events_1.h)]  
  
 Una vez declarado el mapa del evento, se debe definir en el archivo de implementación del control \(.CPP\).  Las siguientes líneas de código definen el mapa del evento, lo que el control desencadena eventos concretos:  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/CPP/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/CPP/mfc-activex-controls-events_3.cpp)]  
  
 Si utiliza el asistente para controles ActiveX MFC para crear el proyecto, agrega automáticamente estas líneas.  Si no utiliza el asistente para controles ActiveX MFC, debe agregar estas líneas manualmente.  
  
 Con la vista de clases, puede agregar eventos comunes compatibles con la clase `COleControl` o los eventos personalizados que se definen.  Para cada nuevo evento, la vista de clases agrega automáticamente la entrada correspondiente a la asignación de eventos del control y el archivo de .IDL del control.  
  
 Otros dos casos tratan eventos en detalle:  
  
-   [Controles ActiveX de MFC: Agregar eventos comunes](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Controles ActiveX de MFC: Agregar eventos personalizados](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)