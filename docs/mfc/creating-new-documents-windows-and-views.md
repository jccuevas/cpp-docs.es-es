---
title: "Crear nuevos documentos, ventanas y vistas | Microsoft Docs"
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
  - "ventanas secundarias, crear MDI"
  - "personalizar objetos predeterminados de MFC"
  - "objetos de documentos, crear"
  - "ventanas de marco [C++], crear"
  - "inicializar vistas"
  - "MDI [C++], crear ventanas"
  - "MDI [C++], ventanas de marco"
  - "MFC [C++], documentos"
  - "MFC [C++], ventanas de marco"
  - "MFC [C++], vistas"
  - "objetos predeterminados de MFC"
  - "objetos predeterminados de MFC, personalizar"
  - "objetos [C++], crear objetos de documentos"
  - "reemplazar, comportamiento de vista predeterminada"
  - "objetos de vista"
  - "objetos de vista, crear"
  - "vistas [C++], inicializar"
  - "vistas [C++], invalidar el comportamiento predeterminado"
  - "Window (objetos) [C++], crear"
  - "ventanas [C++], crear"
  - "ventanas [C++], MDI"
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Crear nuevos documentos, ventanas y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las ilustraciones siguientes proporcionan información general sobre el proceso de creación de documentos, las vistas, las ventanas de marco.  Otros casos que se centran en los objetos que participan proporcionan más detalles.  
  
 Al completar este proceso, los objetos de cooperación existen y almacena punteros entre sí.  Las ilustraciones siguientes muestran la secuencia en la que se crean los objetos.  Puede seguir el orden de la figura a la figura.  
  
 ![Secuencia para crear un documento](../mfc/media/vc387l1.png "vc387L1")  
Secuencia de creación de un documento  
  
 ![Secuencia de creación de ventanas de marco](../mfc/media/vc387l2.png "vc387L2")  
Secuencia de creación de una ventana de marco  
  
 ![Secuencia para crear una vista](../mfc/media/vc387l3.png "vc387L3")  
Secuencia de creación de una vista  
  
 Para obtener información sobre cómo inicializar el marco el nuevo, la vista, y los objetos de la cuadro\- ventana, vea las clases [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) en la referencia de la biblioteca MFC.  Vea también [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md), que explica la creación y procesos de inicialización más bajo su descripción de los comandos estándar de .NET framework para los elementos de `New` y de **Abierta** en el menú de **archivo** .  
  
##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> El que se inicializa Own Adiciones a las clases de These  
 Las ilustraciones anteriores también sugiere puntos en los que puede reemplazar funciones miembro para inicializar los objetos de la aplicación.  Un reemplazo de `OnInitialUpdate` en la clase de vista es el mejor lugar para inicializar la vista.  La llamada de `OnInitialUpdate` aparece inmediatamente después de crear la ventana de marco y la vista dentro de la ventana de marco se adjunta al documento.  Por ejemplo, si la vista es una vista de desplazamiento \(derivada de `CScrollView` en lugar de `CView`\), debe establecer el tamaño de la vista basado en el tamaño documento en la invalidación de `OnInitialUpdate` . \(Este proceso se describe en la clase [CScrollView](../mfc/reference/cscrollview-class.md).\) Puede reemplazar las funciones `OnNewDocument` y `OnOpenDocument` miembro de **CDocument** para proporcionar inicialización específica de la aplicación del documento.  Normalmente, debe reemplazar ambos como un documento se puede crear de dos maneras.  
  
 En la mayoría de los casos, el reemplazo debe llamar a la versión de la clase base.  Para obtener más información, vea funciones denominadas miembro de las clases [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), y [CWinApp](../mfc/reference/cwinapp-class.md) en la referencia de la biblioteca MFC.  
  
## Vea también  
 [Plantillas de documento y el proceso de creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Clear plantillas de documentos](../mfc/document-template-creation.md)   
 [Crear documentos y vistas](../mfc/document-view-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)