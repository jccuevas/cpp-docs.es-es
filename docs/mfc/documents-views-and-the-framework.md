---
title: "Documentos, vistas y el marco | Microsoft Docs"
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
  - "objetos de aplicación [C++], relación con otros objetos MFC"
  - "aplicaciones [MFC]"
  - "objetos de documentos, en relación con otros objetos MFC"
  - "plantillas de documento, objetos de plantilla"
  - "arquitectura documento/vista, acerca de la arquitectura documento/vista"
  - "documentos [C++]"
  - "MFC [C++], marco de trabajo de la aplicación"
  - "MFC [C++], documentos"
  - "MFC [C++], vistas"
  - "relaciones de objeto MFC"
  - "objetos [C++], MFC (aplicaciones)"
  - "objetos de subprocesos"
  - "objetos de vista, relación con otros objetos MFC"
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Documentos, vistas y el marco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el núcleo del marco de trabajo de MFC son los conceptos de documento y de vista.  Un documento es un objeto de datos con el que el usuario interactúa en una sesión de edición.  Crea el comando de `New` o de **Abierta** en el menú de **archivo** y guardado normalmente en un archivo. \(Los documentos estándar de MFC, derivados de la clase **CDocument**, son diferentes de documentos activos y documentos compuestos OLE\). Una vista es un objeto de la ventana a través del cual el usuario interactúa con un documento.  
  
 Los objetos de clave en una aplicación en ejecución son:  
  
-   El documento o documentos.  
  
     La clase document \(derivada de [CDocument](../mfc/reference/cdocument-class.md)\) especifica los datos de aplicación.  
  
     Si desea COM\) en la aplicación, derive la clase de [COleDocument](../mfc/reference/coledocument-class.md) o una de sus clases derivadas, dependiendo del tipo de funcionalidad que necesita.  
  
-   La vista o vistas.  
  
     La clase de vista \(derivada de [CView](../mfc/reference/cview-class.md)\) es ventana de usuario la “en los datos.” Los controles de la clase de vista cómo el usuario ve los datos del documento e interactúa con él.  En algunos casos, puede ser un documento para tener varias vistas de los datos.  
  
     Si necesita desplazarse, derive de [CScrollView](../mfc/reference/cscrollview-class.md).  Si la vista tiene una interfaz de usuario que se encuentra en un recurso de la diálogo\- plantilla, derive de [CFormView](../mfc/reference/cformview-class.md).  Para los datos de texto simple, utilice o deriva de [CEditView](../mfc/reference/ceditview-class.md).  Para una aplicación de acceso a datos formulario\- basada, como un programa de entrada de datos, derive de [CRecordView](../mfc/reference/crecordview-class.md) \(para ODBC\).  También disponibles son clases [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), y [CRichEditView](../mfc/reference/cricheditview-class.md).  
  
-   Las ventanas de marco  
  
     Las vistas son interior mostrará “ventanas de marco de documento”. En una aplicación SDI, la ventana de marco de documento también es la “ventana de marco principal” para la aplicación.  En una aplicación MDI, las ventanas de documento son ventanas secundarias mostradas en una ventana de marco principal.  La clase principal derivada de la cuadro\- ventana especifica los estilos y otras características de las ventanas de marco que contienen vistas.  Si necesita personalizar las ventanas de marco, derive de [CFrameWnd](../mfc/reference/cframewnd-class.md) para personalizar la ventana de marco de documento para las aplicaciones SDI.  Derive de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) para personalizar la ventana de marco principal de las aplicaciones MDI.  También derive una clase de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) para personalizar cada clase distinta de ventanas de marco de documento MDI que admita la aplicación.  
  
-   Plantilla de documento o plantillas  
  
     Una plantilla de documento orquestra la creación de documentos, de vistas, y ventanas de marco.  Una clase determinada de plantilla de documento, derivada de la clase [CDocTemplate](../mfc/reference/cdoctemplate-class.md), crea y administra todos los documentos abiertos de tipo.  Las aplicaciones que admiten más de un tipo de documento tienen plantillas de documento.  Utilice la clase [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) para aplicaciones SDI, o la clase [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) de uso para las aplicaciones MDI.  
  
-   El objeto application  
  
     La clase de aplicación \(derivada de [CWinApp](../mfc/reference/cwinapp-class.md)\) controla todos los objetos arriba y especifica el comportamiento de la aplicación como inicialización y limpieza.  La y sólo el objeto application app crea y administra las plantillas de documento para los tipos de documento que la aplicación admite.  
  
-   Objetos de subprocesos  
  
     Si la aplicación crea subprocesos de ejecución independientes \(por ejemplo, realizar cálculos en segundo plano — usará las clases derivadas de [CWinThread](../mfc/reference/cwinthread-class.md).  [CWinApp](../mfc/reference/cwinapp-class.md) a su vez deriva de `CWinThread` y representa el subproceso principal de la ejecución \(o proceso principal\) en la aplicación.  También puede utilizar MFC en subprocesos secundarios.  
  
 En una aplicación en ejecución, estos objetos de forma cooperativa respondan a las acciones del usuario, el límite entre sí mediante los comandos y otros mensajes.  Un único objeto application administra una o más plantillas de documento.  Cada plantilla de documento crea y administra uno o más documentos \(dependiendo de si la aplicación es SDI o MDI\).  Las vistas de usuario ver y manipular un documento con una vista contenida dentro de una ventana de marco.  La ilustración siguiente muestra las relaciones entre estos objetos para una aplicación SDI.  
  
 ![Objetos de una aplicación SDI en ejecución](../mfc/media/vc386v1.png "vc386V1")  
Objetos de una aplicación SDI en ejecución  
  
 El resto de esta familia de casos explica cómo las herramientas de .NET framework, el asistente para aplicaciones MFC, y los editores de recursos, crean estos objetos, cómo funcionan juntas, y cómo se utiliza en la programación.  Los documentos, las vistas, y las ventanas de marco se explican con más detalle en [Objetos de la ventana](../mfc/window-objects.md) y [Arquitectura documento\/vista](../mfc/document-view-architecture.md).  
  
## Vea también  
 [Usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)