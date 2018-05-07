---
title: Documentos, vistas y el marco de trabajo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2a30f2ccf1963fe2985794a2bf8eca0c49474cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="documents-views-and-the-framework"></a>Documentos, vistas y el marco
En el núcleo del marco de trabajo MFC son los conceptos de documento y vista. Un documento es un objeto de datos con el que interactúa el usuario en una sesión de edición. Que se crea mediante la `New` o **abiertos** comando el **archivo** menú y normalmente se guarda en un archivo. (Los documentos estándar de MFC, derivados de la clase **CDocument**, son diferentes de los documentos activos y los documentos compuestos OLE.) Una vista es un objeto de ventana a través del cual el usuario interactúa con un documento.  
  
 Los objetos de clave en una aplicación en ejecución son:  
  
-   El documento o documentos.  
  
     La clase de documento (derivado de [CDocument](../mfc/reference/cdocument-class.md)) especifica los datos de aplicación.  
  
     Si desea utilizar las funciones OLE de la aplicación, derive su clase de documento de [COleDocument](../mfc/reference/coledocument-class.md) o uno de sus clases derivadas, según el tipo de funcionalidad que necesita.  
  
-   La vista o vistas.  
  
     La clase de vista (derivado de [CView](../mfc/reference/cview-class.md)) es la ventana del usuario"en los datos." La clase de vista controla cómo el usuario ve los datos del documento e interactúa con él. En algunos casos, puede que desee tener varias vistas de los datos de un documento.  
  
     Si necesita desplazamiento, que se derivan de [CScrollView](../mfc/reference/cscrollview-class.md). Si la vista tiene una interfaz de usuario que se encuentra en un recurso de plantilla de cuadro de diálogo, debe derivar de [CFormView](../mfc/reference/cformview-class.md). Para los datos de texto simple, utilizar o derivar de [CEditView](../mfc/reference/ceditview-class.md). Para una aplicación de acceso a datos basado en formularios, como un programa de entrada de datos, que se derivan de [CRecordView](../mfc/reference/crecordview-class.md) (para ODBC). También están disponibles las clases [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), y [CRichEditView](../mfc/reference/cricheditview-class.md).  
  
-   Las ventanas de marco  
  
     Las vistas se muestran dentro de "ventanas de marco de documento". En una aplicación SDI, la ventana de marco de documento es también la "ventana de marco principal" para la aplicación. En una aplicación MDI, las ventanas de documento son ventanas secundarias, aparecerá dentro de una ventana de marco principal. La clase de ventana de marco principal derivada especifica los estilos y otras características de las ventanas de marco que contienen las vistas. Si necesita personalizar las ventanas de marco, derive de [CFrameWnd](../mfc/reference/cframewnd-class.md) para personalizar la ventana de marco de documento para aplicaciones SDI. Derivar de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) para personalizar la ventana de marco principal para aplicaciones MDI. Derivar una clase de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) para personalizar cada distintos tipos de ventanas de marco de documento MDI que admite la aplicación.  
  
-   La plantilla de documento o plantillas  
  
     Una plantilla de documento organiza la creación de documentos, vistas y ventanas de marco. Una clase de plantilla de documento en particular, derivan de la clase [CDocTemplate](../mfc/reference/cdoctemplate-class.md), crea y administra todos los documentos abiertos de un tipo. Las aplicaciones que admiten más de un tipo de documento tienen varias plantillas de documento. Utilice la clase [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) para aplicaciones SDI, o la clase [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para las aplicaciones MDI.  
  
-   El objeto de aplicación  
  
     La clase de aplicación (derivado de [CWinApp](../mfc/reference/cwinapp-class.md)) controla todos los objetos anteriores y especifica el comportamiento de la aplicación, como la inicialización y limpieza. Uno de la aplicación y la aplicación solo el objeto crea y administra las plantillas de documento para la aplicación admite los tipos de cualquier documento.  
  
-   Objetos de subprocesos  
  
     Si la aplicación crea subprocesos independientes de ejecución, por ejemplo, para realizar cálculos en segundo plano, usará las clases que derivan de [CWinThread](../mfc/reference/cwinthread-class.md). [CWinApp](../mfc/reference/cwinapp-class.md) a su vez se deriva de `CWinThread` y representa el subproceso principal de ejecución (o el proceso principal) en la aplicación. También puede utilizar MFC en subprocesos secundarios.  
  
 En una aplicación en ejecución, estos objetos responden a las acciones del usuario, de forma cooperativa unidas mediante comandos y otros mensajes. Un solo objeto aplicación administra una o varias plantillas de documento. Cada plantilla de documento crea y administra uno o varios documentos (dependiendo de si la aplicación es SDI o MDI). El usuario ve y manipula un documento a través de una vista contenida dentro de una ventana de marco. La siguiente ilustración muestra las relaciones entre estos objetos para una aplicación SDI.  
  
 ![Objetos en una aplicación SDI en ejecución](../mfc/media/vc386v1.gif "vc386v1")  
Objetos de una aplicación SDI en ejecución  
  
 El resto de esta familia de artículos explica cómo las herramientas de framework, el Asistente para aplicaciones MFC y los editores de recursos, crean estos objetos, cómo funcionan juntas y cómo usarlos en su programación. Documentos, vistas y ventanas de marco se tratan con más detalle en [Window (objetos)](../mfc/window-objects.md) y [arquitectura documento/vista](../mfc/document-view-architecture.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
