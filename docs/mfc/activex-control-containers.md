---
title: "Contenedores de controles ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++]"
  - "controles OLE [C++], contenedores"
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Contenedores de controles ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un contenedor de controles ActiveX es un contenedor que admite totalmente los controles ActiveX y puede escribirlos en sus propias ventanas o diálogos.  Un control ActiveX es un elemento reutilizable de software que puede usar en muchos proyectos de desarrollo.  Los Controles permiten que el usuario de la aplicación tenga acceso a las bases de datos, controlan datos, y se crean distintas selecciones dentro de las aplicaciones.  Para obtener más información sobre los controles ActiveX, vea el artículo [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md).  
  
 Los contenedores de controles tienen normalmente dos formularios en un proyecto:  
  
-   Cuadros de diálogo y diálogo\- como ventanas como vistas de formulario, donde un control ActiveX se utiliza en alguna parte del cuadro de diálogo.  
  
-   Windows en la aplicación, donde un control ActiveX se utiliza en una barra de herramientas, u otra ubicación en la ventana del usuario.  
  
 El contenedor de controles ActiveX interactúa con el control mediante [métodos](../mfc/mfc-activex-controls-methods.md) expuesto y [propiedades](../mfc/mfc-activex-controls-properties.md).  Estos métodos y propiedades, que pueden obtener acceso y modificar por el contenedor, se realiza a través de una clase contenedora en el proyecto de contenedor de controles ActiveX.  El control ActiveX incrustado también puede interactuar con el contenedor desencadenando \(transporte\) [eventos](../mfc/mfc-activex-controls-events.md) para notificar el contenedor que una acción ha producido.  El contenedor de control puede elegir para representar sobre estas notificaciones o no.  
  
 Artículos adicionales explican varios temas, crear un proyecto de contenedor de controles ActiveX a problemas básicos de implementación relacionados con contenedores de controles ActiveX compilados con Visual C\+\+:  
  
-   [Crear un contenedor de controles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [Contenedores de Controles ActiveX](../mfc/containers-for-activex-controls.md)  
  
-   [Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [Contenedores de controles ActiveX: Insertar un Control en una aplicación contenedora de Control](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [Contenedores de controles ActiveX: Conexión de un control ActiveX con una variable miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [Contenedores de controles ActiveX: Controlar eventos de un control ActiveX](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [Contenedores de controles ActiveX: Vista y propiedades del Control de Modificar](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [Contenedores de controles ActiveX: Controles ActiveX de programación en un contenedor de controles ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [Contenedores de controles ActiveX: Utilizar Controles en un contenedor de no diálogo](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 Para obtener más información sobre cómo utilizar los controles ActiveX en un cuadro de diálogo, vea los temas de [Editor de cuadros de diálogo](../mfc/dialog-editor.md) .  
  
 Para obtener una lista de artículos que explican los detalles de desarrollar controles ActiveX mediante Visual C\+\+ y las clases de controles ActiveX MFC, vea [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md).  Los casos se agrupan por categorías funcionales.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)