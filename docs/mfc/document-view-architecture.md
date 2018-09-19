---
title: Arquitectura de vista-documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9554af9443bbd6a6394789343294630104c96f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350060"
---
# <a name="documentview-architecture"></a>Arquitectura documento/vista
De forma predeterminada, el Asistente para aplicaciones MFC crea una aplicación esqueleto con una clase de documento y una clase de vista. MFC separa la administración de datos en estas dos clases. El documento almacena los datos y administra la impresión de los datos y coordina la actualización de varias vistas de los datos. La vista muestra los datos y administra la interacción del usuario con el mismo, incluida la selección y edición.  
  
 En este modelo, un objeto de documento MFC lee y escribe datos en un almacenamiento persistente. El documento también puede proporcionar una interfaz a los datos dondequiera que residan (como en una base de datos). Un objeto de vista independiente administra la presentación de datos, desde los datos en una ventana de selección de usuarios de representación y edición de los datos. La vista muestra los datos del documento y comunica en el documento, los cambios de datos.  
  
 Aunque puede invalidar o pasar por alto la separación documento/vista fácilmente, hay razones convincentes para seguir este modelo en la mayoría de los casos. Una de las mejores es cuando se necesitan varias vistas del mismo documento, como una hoja de cálculo y una vista de gráfico. El modelo de documento/vista permite a un objeto de vista independiente representan cada vista de los datos, mientras que el código común a todas las vistas (por ejemplo, un motor de cálculo) pueden residir en el documento. El documento también realiza la tarea de actualización de todas las vistas cada vez que cambian los datos.  
  
 La arquitectura documento/vista MFC facilita admitir varias vistas, varios tipos de documentos, ventanas divisoras y otras características valiosas de interfaz de usuario.  
  
 Las partes del marco de trabajo MFC más visible para el usuario y para el programador son el documento y la vista. La mayor parte de su trabajo en el desarrollo de una aplicación con el marco de trabajo entra en escribir las clases de documento y vista. Esta serie de artículos describe:  
  
-   Los fines de documentos, vistas y cómo interactúan en el marco de trabajo.  
  
-   ¿Qué debe hacer para implementarlos.  
  
 La esencia de documento/vista hay cuatro clases importantes:  
  
 El [CDocument](../mfc/reference/cdocument-class.md) (o [COleDocument](../mfc/reference/coledocument-class.md)) clase es compatible con objetos que se usan para almacenar o controlar los datos del programa y proporciona la funcionalidad básica para las clases de documento definida por el programador. Un documento representa la unidad de datos que el usuario normalmente se abre con el comando Abrir en el menú archivo y se guarda con el comando Guardar del menú archivo.  
  
 El [CView](../mfc/reference/cview-class.md) (o uno de sus muchas clases derivadas) proporciona la funcionalidad básica para las clases de vistas definidas por el programador. Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario: la vista presenta una imagen del documento en la pantalla e interpreta proporcionados por el usuario como operaciones sobre el documento. La vista también representa la imagen de vista previa de impresión e imprimir.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md) (o uno de sus variaciones) admite objetos que proporciona el marco que rodea una o varias vistas de un documento.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) (o [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) o [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) es compatible con un objeto que coordina uno o más documentos existentes de un tipo determinado y administra la creación correcta documento, vista y objetos de ventana de marco para ese tipo.  
  
 En la siguiente ilustración muestra la relación entre un documento y su vista.  
  
 ![Vista es la parte del documento que se muestra](../mfc/media/vc379n1.gif "vc379n1")  
Documento y vista  
  
 La implementación de documento/vista en la biblioteca de clases separa los propios datos de su presentación y de operaciones de usuario de los datos. Todos los cambios en los datos se administran a través de la clase de documento. La vista llama a esta interfaz para obtener acceso y actualizar los datos.  
  
 Documentos, sus vistas asociadas y las ventanas de marco de las vistas que se crean mediante una plantilla de documento. La plantilla de documento es responsable de crear y administrar todos los documentos de un tipo de documento.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Un retrato de la arquitectura documento/vista](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [Ventajas de la arquitectura documento/vista](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Clases de documento y vista creadas por el Asistente para aplicaciones](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [Alternativas a la arquitectura documento/vista](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Adición de varias vistas a un solo documento](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [Uso de documentos](../mfc/using-documents.md)  
  
-   [Uso de vistas](../mfc/using-views.md)  
  
-   [Varios tipos de documentos, vistas y ventanas de marco](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Inicializar y limpiar documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [Inicializar sus propias aportaciones a las clases de documento y vista](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [Utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [Ejemplos](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [Ventanas de marco](../mfc/frame-windows.md)   
 [Plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Creación de documento/vista](../mfc/document-view-creation.md)   
 [Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

