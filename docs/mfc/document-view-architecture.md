---
title: "Arquitectura documento/vista | Microsoft Docs"
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
  - "CDocument (clase)"
  - "CView (clase), vista de arquitectura"
  - "objetos de documentos"
  - "objetos de documentos, arquitectura documento/vista"
  - "objetos de documentos, modelo documento/vista de MFC"
  - "documentos, modelo documento/vista de MFC"
  - "MFC, documentos"
  - "MFC, vistas"
  - "vistas, modelo documento/vista de MFC"
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Arquitectura documento/vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, el asistente para aplicaciones MFC crea un esquema de la aplicación con una clase de documento y una clase de vista.  MFC separa la administración de datos en estas dos clases.  El documento almacena los datos y administra imprimir los datos y las coordenadas que actualizan varias vistas de los datos.  La vista muestra los datos y administra la interacción del usuario con ella, como selección y edición.  
  
 En este modelo, los datos de lee y escribe el objeto document de MFC el almacenamiento persistente.  El documento puede proporcionar una interfaz a los datos donde resida \(como una base de datos\).  Un objeto de vista independiente administra la presentación de datos, para generar los datos de una ventana en la selección del usuario y de editarlos de datos.  La vista obtiene datos de presentación del documento y comunica al documento cualquier cambio de los datos.  
  
 Aunque puede fácilmente invalidar u omitir la separación de documentos y vistas, hay motivos para seguir este modelo en la mayoría de los casos.  Uno de mejor es cuando necesita varias vistas del mismo documento, como una hoja de cálculo y una vista.  El modelo de documento y vista permite un objeto de vista independiente representar cada vista de los datos, como el campo común de código a todo ver \(por ejemplo un motor de cálculo\) puede residir en el documento.  El documento también adquiere la tarea para actualizar todas las vistas siempre que los cambios de datos.  
  
 La arquitectura documento\/vista de MFC facilita que admite varias vistas, los tipos de documento múltiples, las ventanas divisoras, y otras características valiosas de la interfaz de usuario.  
  
 Las partes del marco de trabajo de MFC más visible para el usuario y se, el programador, son el documento y.  La mayor parte del trabajo de desarrollar una aplicación con el marco entra la escritura de las clases de documento y de la vista.  Esta familia de artículo se describe:  
  
-   Fines de documentos y vistas y cómo interactúan en el marco.  
  
-   Qué debe hacer para implementarlo.  
  
 En el núcleo de documento y vista son cuatro clases clave:  
  
 La clase de [CDocument](../mfc/reference/cdocument-class.md) \(o [COleDocument](../mfc/reference/coledocument-class.md)\) admite los objetos utilizados para almacenar o controlar los datos del programa y proporciona la funcionalidad básica para las clases programador\- definido del documento.  Un documento representa la unidad de datos que el usuario abre normalmente con el comando abierto en el menú archivo y guarda con el comando Save en el menú archivo.  
  
 [CView](../mfc/reference/cview-class.md) \(o una de sus muchas clases derivadas\) proporciona la funcionalidad básica para las clases programador\- definido de la vista.  Una vista está asociado a un documento y actúa como intermediario entre el documento y el usuario: la vista representa una imagen del documento en la pantalla e interpreta los datos proporcionados por el usuario como operaciones sobre el documento.  La vista también genera la imagen para la impresión y vista previa de impresión.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md) \(o una de sus variantes\) admite objetos que proporciona el cuadro alrededor de una o más vistas de un documento.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) \(o [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) o [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)\) admite un objeto que las coordenadas uno o más documentos existentes de un tipo determinado y administra crear el documento, la vista, y los objetos correctos de la ventana de marco para ese tipo.  
  
 La ilustración siguiente muestra la relación entre un documento y su vista.  
  
 ![La vista es la parte del documento que se muestra](../mfc/media/vc379n1.png "vc379N1")  
Documento y vista  
  
 La aplicación de documento y vista en la biblioteca de clases separa los propios datos de la pantalla y operaciones de usuario en los datos.  Todos los cambios en los datos se administran a través de la clase del documento.  La vista llama a esta interfaz para obtener acceso y actualizar los datos.  
  
 Documentos, sus vistas asociadas, y las ventanas de marco que el cuadro vistas es creado por una plantilla de documento.  Plantilla de documento es responsable de crear y administrar todos los documentos de un tipo de documento.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Un orientación de la arquitectura documento\/vista](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [Ventajas de la arquitectura documento\/vista](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Clases de documento y vista creada por el Asistente para aplicaciones](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [Alternativas a la arquitectura documento\/vista](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Vistas de agregar varios a un documento Single](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [Utilizar documentos](../mfc/using-documents.md)  
  
-   [Con las vistas](../mfc/using-views.md)  
  
-   [Tipos de documento, vistas, y cuadro varias Windows](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [El inicializar y limpiar el documentos ni vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [Inicialice poseen adiciones a las clases & de la vista del documento](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [Utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [Ejemplos](../top/visual-cpp-samples.md)  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [Ventanas de marco](../mfc/frame-windows.md)   
 [Plantillas de documento y el proceso de creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Crear documentos y vistas](../mfc/document-view-creation.md)   
 [Crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)