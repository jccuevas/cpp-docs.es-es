---
title: Arquitectura de vista-documento
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
ms.openlocfilehash: d1b1f80f44fdc66a3174ea75c15e139f98a4520b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775548"
---
# <a name="documentview-architecture"></a>Arquitectura documento/vista

De forma predeterminada, el Asistente para aplicaciones MFC crea una esqueleto de la aplicación con una clase de documento y una clase de vista. MFC separa la administración de datos en estas dos clases. El documento almacena los datos y administra la impresión de los datos y coordina la actualización de varias vistas de los datos. La vista muestra los datos y administra la interacción del usuario con él, incluida la selección y edición.

En este modelo, un objeto de documento MFC lee y escribe datos en un almacenamiento persistente. El documento también puede proporcionar una interfaz a los datos dondequiera que residan (como en una base de datos). Un objeto de vista independiente administra la presentación de datos, de procesamiento de datos en una ventana de selección del usuario y la edición de datos. La vista muestra los datos del documento y comunica con el documento que cambie algún dato.

Aunque puede invalidar fácilmente o pasar por alto la separación de documento/vista, hay razones convincentes para seguir este modelo en la mayoría de los casos. Una de las mejores es cuando necesite varias vistas del mismo documento, como una hoja de cálculo y una vista de gráfico. El modelo de documento/vista permite a un objeto de vista independiente representan cada vista de los datos, mientras que el código común a todas las vistas (por ejemplo, un motor de cálculo) pueden residir en el documento. El documento también realiza la tarea de actualización cada vez que cambian los datos de todas las vistas.

La arquitectura documento/vista MFC facilita la compatibilidad con varias vistas, varios tipos de documentos, ventanas divisoras y otras características de interfaz de usuario valiosos.

Las partes de framework MFC más visible para el usuario y para el programador, son el documento y vista. La mayoría del trabajo de desarrollo de una aplicación con el marco de trabajo entra en escribir las clases de documento y vista. Esta serie de artículos describe:

- Los propósitos de documentos y vistas, y cómo interactúan en el marco de trabajo.

- ¿Qué debe hacer para implementarlos.

En el corazón de documento/vista hay cuatro clases importantes:

El [CDocument](../mfc/reference/cdocument-class.md) (o [COleDocument](../mfc/reference/coledocument-class.md)) clase es compatible con los objetos utilizados para almacenar o controlar los datos del programa y proporciona la funcionalidad básica para las clases de documento definido por el programador. Un documento representa la unidad de datos que el usuario normalmente se abre con el comando Abrir en el menú archivo y guarda con el comando Guardar del menú archivo.

El [CView](../mfc/reference/cview-class.md) (o uno de sus clases derivadas) proporciona la funcionalidad básica para las clases de vista definidos por el programador. Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario: la vista presenta una imagen del documento en la pantalla y se interpreta la entrada del usuario como operaciones sobre el documento. La vista también presenta la imagen de vista previa de impresión e imprimir.

[CFrameWnd](../mfc/reference/cframewnd-class.md) (o uno de sus variaciones) admite objetos que proporciona el marco alrededor de una o varias vistas de un documento.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md) (o [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) o [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) es compatible con un objeto que uno o varios documentos existentes de un tipo determinado de coordina y administra la creación de la correcta documento, vista y los objetos de ventana de marco para ese tipo.

En la siguiente ilustración muestra la relación entre un documento y su vista.

![La vista es la parte del documento que se muestra](../mfc/media/vc379n1.gif "vista es la parte del documento que se muestra") <br/>
Documento y vista

La implementación de documento/vista en la biblioteca de clases separa los propios datos de su presentación y de los datos de las operaciones de usuario. Todos los cambios en los datos se administran a través de la clase de documento. La vista se llama a esta interfaz para obtener acceso y actualizar los datos.

Documentos, sus vistas asociadas y las ventanas de marco de las vistas que se crean mediante una plantilla de documento. La plantilla de documento es responsable de crear y administrar todos los documentos de un tipo de documento.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Un retrato de la arquitectura documento/vista](../mfc/a-portrait-of-the-document-view-architecture.md)

- [Ventajas de la arquitectura documento/vista](../mfc/advantages-of-the-document-view-architecture.md)

- [Clases de documento y vista creadas por el Asistente para aplicaciones](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternativas a la arquitectura documento/vista](../mfc/alternatives-to-the-document-view-architecture.md)

- [Adición de varias vistas a un solo documento](../mfc/adding-multiple-views-to-a-single-document.md)

- [Uso de documentos](../mfc/using-documents.md)

- [Uso de vistas](../mfc/using-views.md)

- [Varios tipos de documentos, vistas y ventanas de marco](../mfc/multiple-document-types-views-and-frame-windows.md)

- [Inicializar y limpiar documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)

- [Inicializar sus propias aportaciones a las clases de documento y vista](../mfc/creating-new-documents-windows-and-views.md)

- [Uso de clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Uso de clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Muestras](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[Windows](../mfc/windows.md)<br/>
[Ventanas de marco](../mfc/frame-windows.md)<br/>
[Las plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Crear documentos y vistas](../mfc/document-view-creation.md)<br/>
[Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)
