---
title: Contenedores de controles ActiveX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee24d39c8769eaf2216ca4f64b9856b778a51ac7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers"></a>Contenedores de controles ActiveX
Un contenedor de controles ActiveX es un contenedor que es totalmente compatible con controles ActiveX y puede incorporarlos a sus propias ventanas o cuadros de diálogo. Un control ActiveX es un elemento de software reutilizable que puede usar en muchos proyectos de desarrollo. Controles permiten a tener acceso a las bases de datos, supervisar datos y realizar varias selecciones dentro de las aplicaciones de usuario de la aplicación. Para obtener más información sobre los controles ActiveX, vea el artículo [controles ActiveX MFC](../mfc/mfc-activex-controls.md).  
  
 Contenedores de controles suelen tardar dos formas en un proyecto:  
  
-   Cuadro de diálogo ventanas como vistas de formulario, donde se utiliza en algún lugar un control ActiveX en el cuadro de diálogo y cuadros de diálogo.  
  
-   Windows en una aplicación, donde se utiliza un control ActiveX en una barra de herramientas, o en otra ubicación en la ventana de usuario.  
  
 Expone el contenedor del control interactúa con el control a través de ActiveX [métodos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md). Estos métodos y propiedades, que se pueden acceder y modificar el contenedor del control, se obtiene acceso a través de una clase de contenedor en el proyecto de contenedor de controles ActiveX. El control ActiveX incrustado también puede interactuar con el contenedor activando (enviar) [eventos](../mfc/mfc-activex-controls-events.md) para notificar al contenedor que se ha producido una acción. Puede elegir el contenedor del control para que actúe sobre estas notificaciones o no.  
  
 Artículos adicionales describen temas diversos, desde crear un proyecto de contenedor del control ActiveX a aspectos básicos de implementación relacionados con contenedores de controles ActiveX creados con Visual C++:  
  
-   [Creación de un contenedor de controles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [Contenedores de controles ActiveX](../mfc/containers-for-activex-controls.md)  
  
-   [Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [Contenedores de controles ActiveX: Insertar un control en una aplicación de contenedor de controles](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [Contenedores de controles ActiveX: Conectar un control ActiveX a una variable de miembro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [Contenedores de controles ActiveX: Controlar el control de eventos de un control ActiveX](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [Contenedores de controles ActiveX: Ver y modificar propiedades de los controles](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [Contenedores de controles ActiveX: Programar controles ActiveX en un contenedor de controles ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 Para obtener más información sobre el uso de controles ActiveX en un cuadro de diálogo, vea el [Editor de cuadro de diálogo](../windows/dialog-editor.md) temas.  
  
 Para obtener una lista de artículos que explican los detalles sobre el desarrollo de controles ActiveX utilizando Visual C++ y las clases de controles ActiveX en MFC, vea [controles ActiveX en MFC](../mfc/mfc-activex-controls.md). Los artículos se agrupan por categorías funcionales.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

