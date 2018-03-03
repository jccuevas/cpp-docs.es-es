---
title: Ventanas de marco | Documentos de Microsoft
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
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 14dabd345f47b064f78a4e9a3dede834bddeb9d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="frame-windows"></a>Ventanas de marco
Cuando una aplicación se ejecuta en Windows, el usuario interactúa con documentos que se muestran en ventanas de marco. Una ventana de marco de documento tiene dos componentes principales: el marco y el contenido que lo rodea. Una ventana de marco de documento puede ser un [interfaz de único documento](../mfc/sdi-and-mdi.md) ventana de marco (SDI) o un [interfaz de múltiples documentos](../mfc/sdi-and-mdi.md) ventana secundaria (MDI). Windows administra la mayor parte de la interacción del usuario con la ventana de marco: mover y cambiar el tamaño de la ventana, cerrarla y minimizar y maximizar se. Administrar el contenido dentro del marco.  
  
## <a name="frame-windows-and-views"></a>Vistas y ventanas de marco  
 El marco de trabajo MFC utiliza ventanas de marco para contener vistas. Los dos componentes: marco de contenido, se representa y administrado mediante dos clases diferentes de MFC. Una clase de ventana de marco administra el marco, y una clase de vista administra el contenido. La ventana de vista es un elemento secundario de la ventana de marco. Dibujo y otra interacción del usuario con el documento tienen lugar en el área de cliente de la vista, no el área de cliente de la ventana de marco. La ventana de marco proporciona un marco visible alrededor de una vista, junto con una barra de título y controles de ventana estándar, como un menú de control, botones Minimizar y maximizar la ventana y controles para cambiar el tamaño de la ventana. El "contenido" constan del área de cliente de la ventana, que está totalmente ocupado por una ventana secundaria, la vista. En la siguiente ilustración muestra la relación entre una ventana de marco y una vista.  
  
 ![Vista de la ventana de marco](../mfc/media/vc37fx1.gif "vc37fx1")  
Vista y ventana de marco  
  
## <a name="frame-windows-and-splitter-windows"></a>Ventanas de marco y ventanas divisoras  
 Otra distribución común es para que la ventana de marco enmarcar varias vistas, normalmente mediante un [ventana divisora](../mfc/multiple-document-types-views-and-frame-windows.md). En una ventana divisora, el área de cliente de la ventana de marco está ocupado por una ventana divisora, que a su vez tiene varias ventanas secundarias, denominadas paneles, que son vistas.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
 **Temas de ventana de marco general**  
  
-   [Window (objetos)](../mfc/window-objects.md)  
  
-   [Clases de ventana de marco](../mfc/frame-window-classes.md)  
  
-   [Las clases de ventana de marco creadas por el Asistente para aplicaciones](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)  
  
-   [¿Qué ventanas de marco](../mfc/what-frame-windows-do.md)  
  
 **Temas sobre el uso de ventanas de marco**  
  
-   [Usar ventanas de marco](../mfc/using-frame-windows.md)  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Destruir ventanas de marco](../mfc/destroying-frame-windows.md)  
  
-   [Administrar ventanas secundarias MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Administrar la vista actual](../mfc/managing-the-current-view.md) en una ventana de marco que contiene más de una vista  
  
-   [Administrar menús, barras de control y aceleradores (otros objetos que comparten el espacio de la ventana de marco)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **Temas sobre las capacidades de ventana de marco especiales**  
  
-   [Arrastrar y colocar archivos](../mfc/dragging-and-dropping-files-in-a-frame-window.md) desde el Explorador de archivos o administrador de archivos en una ventana de marco  
  
-   [Responder al intercambio dinámico de datos (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [Estados semimodales: ayuda contextual de Windows (orquestar otras acciones de ventana)](../mfc/orchestrating-other-window-actions.md)  
  
-   [Estados semimodales: vista previa de impresión y (orquestar otras acciones de ventana)](../mfc/orchestrating-other-window-actions.md)  
  
 **Temas sobre otros tipos de ventanas**  
  
-   [Uso de vistas](../mfc/using-views.md)  
  
-   [Cuadros de diálogo](../mfc/dialog-boxes.md)  
  
-   [Controles](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows](../mfc/windows.md)

