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
ms.openlocfilehash: 17956c0b175e978c6e4e2fefcdad5f744929d457
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621834"
---
# <a name="documents-views-and-the-framework"></a>Documentos, vistas y el marco

En el corazón del marco de trabajo de MFC se encuentran los conceptos de documento y vista. Un documento es un objeto de datos con el que el usuario interactúa en una sesión de edición. Se crea mediante el comando **nuevo** o **abrir** en el menú **archivo** y normalmente se guarda en un archivo. (Los documentos de MFC estándar, que se derivan de la clase `CDocument` , son diferentes de los documentos activos y los documentos compuestos OLE). Una vista es un objeto de ventana a través del que el usuario interactúa con un documento.

Los objetos clave de una aplicación en ejecución son:

- Documento o documentos.

   La clase de documento (derivada de [CDocument](reference/cdocument-class.md)) especifica los datos de la aplicación.

   Si desea usar la funcionalidad OLE en la aplicación, derive la clase de documento de [COleDocument](reference/coledocument-class.md) o de una de sus clases derivadas, dependiendo del tipo de funcionalidad que necesite.

- Vista o vistas.

   La clase View (derivada de [CView](reference/cview-class.md)) es la "ventana de los datos" del usuario. La clase de vista controla cómo el usuario ve los datos del documento e interactúa con él. En algunos casos, puede que desee que un documento tenga varias vistas de los datos.

   Si necesita desplazarse, derive de [CScrollView](reference/cscrollview-class.md). Si la vista tiene una interfaz de usuario que se coloca en un recurso de plantilla de cuadro de diálogo, derive de [CFormView](reference/cformview-class.md). Para datos de texto simples, use o derive de [CEditView](reference/ceditview-class.md). Para una aplicación de acceso a datos basada en formularios, como un programa de entrada de datos, derive de [CRecordView](reference/crecordview-class.md) (para ODBC). También están disponibles las clases [CTreeView](reference/ctreeview-class.md), [CListView](reference/clistview-class.md)y [CRichEditView](reference/cricheditview-class.md).

- Ventanas de marco

   Las vistas se muestran dentro de "ventanas de marco de documento". En una aplicación SDI, la ventana de marco de documento es también la "ventana de marco principal" de la aplicación. En una aplicación MDI, las ventanas de documento son ventanas secundarias que se muestran en una ventana de marco principal. La clase de ventana de marco principal derivada especifica los estilos y otras características de las ventanas de marco que contienen las vistas. Si necesita personalizar las ventanas de marco, derive de [CFrameWnd](reference/cframewnd-class.md) para personalizar la ventana de marco de documento para aplicaciones SDI. Derive de [CMDIFrameWnd](reference/cmdiframewnd-class.md) para personalizar la ventana de marco principal de las aplicaciones MDI. Derive también una clase de [CMDIChildWnd](reference/cmdichildwnd-class.md) para personalizar cada clase distinta de ventanas de marco de documento MDI que admita la aplicación.

- Plantilla o plantillas de documento

   Una plantilla de documento organiza la creación de documentos, vistas y ventanas de marco. Una clase de plantilla de documento determinada, derivada de la clase [CDocTemplate](reference/cdoctemplate-class.md), crea y administra todos los documentos abiertos de un tipo. Las aplicaciones que admiten más de un tipo de documento tienen varias plantillas de documento. Use la clase [CSingleDocTemplate](reference/csingledoctemplate-class.md) para las aplicaciones SDI o use la clase [CMULTIDOCTEMPLATE](reference/cmultidoctemplate-class.md) para aplicaciones MDI.

- El objeto Application

   La clase de aplicación (derivada de [CWinApp](reference/cwinapp-class.md)) controla todos los objetos anteriores y especifica el comportamiento de la aplicación, como la inicialización y la limpieza. El objeto de aplicación único y único de la aplicación crea y administra las plantillas de documento para cualquier tipo de documento admitido por la aplicación.

- Objetos de subproceso

   Si la aplicación crea subprocesos independientes de ejecución (por ejemplo, para realizar cálculos en segundo plano), usará clases derivadas de [CWinThread](reference/cwinthread-class.md). [CWinApp](reference/cwinapp-class.md) se deriva de `CWinThread` y representa el subproceso principal de ejecución (o el proceso principal) en la aplicación. También puede usar MFC en subprocesos secundarios.

En una aplicación en ejecución, estos objetos responden de forma cooperativa a las acciones del usuario, enlazadas entre sí mediante comandos y otros mensajes. Un único objeto de aplicación administra una o varias plantillas de documento. Cada plantilla de documento crea y administra uno o más documentos (en función de si la aplicación es SDI o MDI). El usuario ve y manipula un documento a través de una vista contenida dentro de una ventana de marco. En la siguiente ilustración se muestran las relaciones entre estos objetos para una aplicación SDI.

![Objetos en una aplicación SDI en ejecución](../mfc/media/vc386v1.gif "Objetos de una aplicación SDI en ejecución") <br/>
Objetos de una aplicación SDI en ejecución

El resto de esta familia de artículos explica cómo las herramientas de marco de trabajo, el Asistente para aplicaciones MFC y los editores de recursos crean estos objetos, cómo funcionan juntos y cómo se usan en la programación. Los documentos, las vistas y las ventanas de marco se describen con más detalle en [objetos de ventana](window-objects.md) y en la arquitectura de [documento y vista](document-view-architecture.md).

## <a name="see-also"></a>Consulte también

[Uso de las clases para escribir aplicaciones para Windows](using-the-classes-to-write-applications-for-windows.md)
