---
title: Documentos, vistas y el marco
ms.date: 11/19/2018
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
ms.openlocfilehash: 799035976ea55988a635f7dc9b667e87c48d8f7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273509"
---
# <a name="documents-views-and-the-framework"></a>Documentos, vistas y el marco

En el corazón de marco de trabajo MFC son los conceptos de documento y vista. Un documento es un objeto de datos con el que interactúa el usuario en una sesión de edición. Lo crea el **New** o **abierto** comando el **archivo** menú y normalmente se guarda en un archivo. (Los documentos estándar de MFC, derivados de la clase `CDocument`, son diferentes de documentos activos y los documentos compuestos OLE.) Una vista es un objeto de ventana a través del cual el usuario interactúa con un documento.

Los objetos de clave en una aplicación en ejecución son:

- El documento o documentos.

   La clase de documento (derivado de [CDocument](../mfc/reference/cdocument-class.md)) especifica los datos de la aplicación.

   Si desea la funcionalidad OLE en la aplicación, derive la clase de documento de [COleDocument](../mfc/reference/coledocument-class.md) o uno de sus clases derivadas, según el tipo de funcionalidad que necesita.

- La vista o vistas.

   La clase de vista (derivado de [CView](../mfc/reference/cview-class.md)) es la ventana del usuario"en los datos." La clase de vista controla cómo el usuario ve los datos del documento e interactúa con él. En algunos casos, puede tener varias vistas de los datos de un documento.

   Si necesita el desplazamiento, que se derivan de [CScrollView](../mfc/reference/cscrollview-class.md). Si la vista tiene una interfaz de usuario que está colocada en un recurso de plantilla de cuadro de diálogo, debe derivar de [CFormView](../mfc/reference/cformview-class.md). Para los datos de texto simple, usar o derivar de [CEditView](../mfc/reference/ceditview-class.md). Para una aplicación de acceso a datos basada en formularios, como un programa de entrada de datos, se deriva de [CRecordView](../mfc/reference/crecordview-class.md) (para ODBC). También están disponibles las clases [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), y [CRichEditView](../mfc/reference/cricheditview-class.md).

- Las ventanas de marco

   Las vistas se muestran dentro de "ventanas de marco de documento". En una aplicación SDI, la ventana de marco de documento también es la "ventana de marco principal" de la aplicación. En una aplicación MDI, ventanas de documento son ventanas secundarias que se muestran dentro de una ventana de marco principal. La clase de ventana de marco principal derivada especifica los estilos y otras características de las ventanas de marco que contienen las vistas. Si necesita personalizar las ventanas de marco, que se derivan de [CFrameWnd](../mfc/reference/cframewnd-class.md) para personalizar la ventana de marco de documento para las aplicaciones SDI. Derivar de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) para personalizar la ventana de marco principal para aplicaciones MDI. También derivar una clase de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) para personalizar cada distintos tipos de ventanas de marco de documento MDI que admite la aplicación.

- Las plantillas o una plantilla de documento

   Una plantilla de documento organiza la creación de documentos, vistas y ventanas de marco. Una clase de plantilla de documento en particular, deriva de la clase [CDocTemplate](../mfc/reference/cdoctemplate-class.md), crea y administra todos los documentos abiertos de un tipo. Las aplicaciones que admiten más de un tipo de documento tienen varias plantillas de documento. Utilice la clase [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) para las aplicaciones SDI, o la clase [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para aplicaciones MDI.

- El objeto de aplicación

   La clase de aplicación (derivado de [CWinApp](../mfc/reference/cwinapp-class.md)) controla todos los objetos anteriores y especifica el comportamiento de la aplicación, como la inicialización y limpieza. Crea y administra las plantillas de documento para cualquier documento de la aplicación admite los tipos de objeto uno de la aplicación y la única aplicación.

- Objetos de subprocesos

   Si la aplicación crea subprocesos de ejecución aislados, por ejemplo, para realizar cálculos en segundo plano, deberá usar las clases derivadas de [CWinThread](../mfc/reference/cwinthread-class.md). [CWinApp](../mfc/reference/cwinapp-class.md) a su vez se deriva `CWinThread` y representa el subproceso principal de ejecución (o el proceso principal) en la aplicación. También puede utilizar MFC en subprocesos secundarios.

En una aplicación en ejecución, estos objetos responden de forma cooperativa a acciones del usuario, enlazadas mediante los comandos y otros mensajes. Un solo objeto aplicación administra una o varias plantillas de documento. Cada plantilla de documento crea y administra uno o varios documentos (dependiendo de si la aplicación es SDI o MDI). El usuario ve y manipula documentos a través de una vista contenida dentro de una ventana de marco. La siguiente ilustración muestra las relaciones entre estos objetos para una aplicación SDI.

![Los objetos en una aplicación SDI en ejecución](../mfc/media/vc386v1.gif "objetos en una aplicación SDI en ejecución") <br/>
Objetos de una aplicación SDI en ejecución

El resto de esta serie de artículos explica cómo las herramientas de marco de trabajo, el Asistente para aplicaciones MFC y los editores de recursos, crean estos objetos, cómo funcionan y cómo usarlos en su programación. Documentos, vistas y ventanas de marco se tratan con más detalle en [Window (objetos)](../mfc/window-objects.md) y [arquitectura documento/vista](../mfc/document-view-architecture.md).

## <a name="see-also"></a>Vea también

[Uso de las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
