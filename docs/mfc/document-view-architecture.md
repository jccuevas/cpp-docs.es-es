---
title: Arquitectura de vistas y documentos
ms.date: 11/19/2018
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
ms.openlocfilehash: a74aeba651d385cf3a5386e94ec20e4e56b7cd57
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624784"
---
# <a name="documentview-architecture"></a>Arquitectura documento/vista

De forma predeterminada, el Asistente para aplicaciones MFC crea un esqueleto de aplicación con una clase de documento y una clase de vista. MFC separa la administración de datos en estas dos clases. El documento almacena los datos y administra la impresión de datos y coordina la actualización de varias vistas de los datos. La vista muestra los datos y administra la interacción del usuario con él, incluida la selección y la edición.

En este modelo, un objeto de documento MFC Lee y escribe datos en el almacenamiento persistente. El documento también puede proporcionar una interfaz a los datos dondequiera que se encuentren (por ejemplo, en una base de datos). Un objeto de vista independiente administra la presentación de datos, desde la representación de los datos de una ventana hasta la selección del usuario y la edición de los datos. La vista obtiene datos de visualización del documento y se comunica con el documento cualquier cambio que se realice en los datos.

Aunque puede invalidar u omitir fácilmente la separación de documentos y vistas, existen razones atractivas para seguir este modelo en la mayoría de los casos. Uno de los mejores es cuando necesita varias vistas del mismo documento, como una hoja de cálculo y una vista de gráfico. El modelo documento/vista permite a un objeto de vista independiente representar cada vista de los datos, mientras que el código común a todas las vistas (como un motor de cálculo) puede residir en el documento. El documento también realiza la tarea de actualizar todas las vistas cada vez que cambian los datos.

La arquitectura de vista/documento de MFC facilita la compatibilidad con varias vistas, varios tipos de documentos, ventanas divisoras y otras características valiosas de la interfaz de usuario.

Las partes del marco de trabajo de MFC más visibles tanto para el usuario como para usted, el programador, son el documento y la vista. La mayor parte del trabajo en el desarrollo de una aplicación con el marco entra en la escritura de las clases de documento y vista. En esta familia de artículos se describe:

- Los propósitos de los documentos y las vistas, y cómo interactúan en el marco.

- Lo que debe hacer para implementarlos.

En el corazón del documento o la vista hay cuatro clases clave:

La clase [CDocument](reference/cdocument-class.md) (o [COleDocument](reference/coledocument-class.md)) admite objetos que se usan para almacenar o controlar los datos del programa y proporciona la funcionalidad básica para las clases de documento definidas por el programador. Un documento representa la unidad de datos que el usuario suele abrir con el comando abrir en el menú Archivo y se guarda con el comando Guardar del menú archivo.

[CView](reference/cview-class.md) (o una de sus muchas clases derivadas) proporciona la funcionalidad básica para las clases de vista definidas por el programador. Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario: la vista representa una imagen del documento en la pantalla e interpreta la entrada del usuario como operaciones en el documento. La vista también representa la imagen para la impresión y la vista previa de impresión.

[CFrameWnd](reference/cframewnd-class.md) (o una de sus variaciones) admite objetos que proporcionan el marco en torno a una o varias vistas de un documento.

[CDocTemplate](reference/cdoctemplate-class.md) (o [CSingleDocTemplate](reference/csingledoctemplate-class.md) o [CMultiDocTemplate](reference/cmultidoctemplate-class.md)) admite un objeto que coordina uno o más documentos existentes de un tipo determinado y administra la creación de los objetos de documento, vista y ventana de marco correctos para ese tipo.

En la siguiente ilustración se muestra la relación entre un documento y su vista.

![La vista es la parte del documento que se muestra](../mfc/media/vc379n1.gif "La vista es la parte del documento que se muestra") <br/>
Documento y vista

La implementación de documento/vista en la biblioteca de clases separa los datos de la pantalla y de las operaciones de usuario en los datos. Todos los cambios en los datos se administran a través de la clase Document. La vista llama a esta interfaz para obtener acceso a los datos y actualizarlos.

Los documentos, sus vistas asociadas y las ventanas de marco que enmarcan las vistas se crean mediante una plantilla de documento. La plantilla de documento es responsable de la creación y administración de todos los documentos de un tipo de documento.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Un retrato de la arquitectura documento/vista](a-portrait-of-the-document-view-architecture.md)

- [Ventajas de la arquitectura documento/vista](advantages-of-the-document-view-architecture.md)

- [Clases de documento y vista creadas por el Asistente para aplicaciones](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternativas a la arquitectura documento/vista](alternatives-to-the-document-view-architecture.md)

- [Agregar varias vistas a un solo documento](adding-multiple-views-to-a-single-document.md)

- [Usar documentos](using-documents.md)

- [Usar vistas](using-views.md)

- [Varios tipos de documentos, vistas y ventanas de marco](multiple-document-types-views-and-frame-windows.md)

- [Inicializar y limpiar documentos y vistas](initializing-and-cleaning-up-documents-and-views.md)

- [Inicialice sus propias adiciones a las clases de vista de & de documentos](creating-new-documents-windows-and-views.md)

- [Utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Muestras](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[Ventanas de marco](frame-windows.md)<br/>
[Plantillas de documento y el proceso de creación de documentos y vistas](document-templates-and-the-document-view-creation-process.md)<br/>
[Crear documentos y vistas](document-view-creation.md)<br/>
[Crear nuevos documentos, ventanas y vistas](creating-new-documents-windows-and-views.md)
