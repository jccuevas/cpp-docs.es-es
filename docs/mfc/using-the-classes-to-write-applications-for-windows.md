---
title: "Usar las clases para escribir aplicaciones para Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [OLE], marco de trabajo de la aplicación MFC"
  - "aplicaciones de base de datos [C++], crear"
  - "MFC [C++], desarrollo de aplicaciones"
  - "controles ActiveX en MFC, crear"
  - "aplicaciones OLE [C++], marco de trabajo de la aplicación MFC"
  - "aplicaciones Windows [C++], marco de trabajo de la aplicación MFC"
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar las clases para escribir aplicaciones para Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tomadas juntas, las clases de la biblioteca de \(MFC\) de la clase de la Microsoft foundation class constituyen un “marco de aplicación”, en la que se compila una aplicación para el sistema operativo Windows.  En un nivel muy general, el marco define la estructura de una aplicación y las implementaciones estándar de la interfaz de usuario de las fuentes que se pueden colocar sobre el esqueleto.  El trabajo como desarrollador es rellenar el resto de esqueleto, que son las acciones específicas de la aplicación.  Puede obtener una ventaja mediante el asistente para aplicaciones MFC para crear los archivos de una aplicación bastante completa inicial.  Utilice los editores de recursos de Microsoft Visual C\+\+ para diseñar los elementos de la interfaz de usuario visualmente, los comandos de la vista de clases para conectar los elementos al código, y la biblioteca de clases para implementar la lógica específica de la aplicación.  
  
 La versión 3.0 y posteriores de MFC admite la programación para plataformas Win32, incluidos Microsoft Windows 95 y versiones posteriores, y las versiones Windows NT 3,51 y posterior.  Compatibilidad con MFC Win32 incluye multithreading.  Utilice la versión 1.5*x* si necesita hacer la programación de 16 bits.  
  
 Esta familia de casos muestra información general acerca de aplicación.  También se describen los objetos principales que constituyen la aplicación y cómo se crean.  Entre los temas cubiertos en estos casos son los siguientes:  
  
-   [El marco](../mfc/framework-mfc.md).  
  
-   División del trabajo entre el marco y el código, como se describe en [La compilación en el marco](../mfc/building-on-the-framework.md).  
  
-   [La clase de aplicación](../mfc/cwinapp-the-application-class.md), que encapsula la funcionalidad en la aplicación.  
  
-   Cómo [plantillas de documento](../mfc/document-templates-and-the-document-view-creation-process.md) crea y administra los documentos y las vistas y ventanas asociadas del cuadro.  
  
-   Clase [CWnd](../mfc/window-objects.md), la clase base de la raíz de todas las ventanas.  
  
-   [Objetos gráficos](../mfc/graphic-objects.md), como lápices y pinceles.  
  
 Otras partes de inclusión de marco de trabajo:  
  
-   [Objetos de la ventana: Introducción](../mfc/window-objects.md)  
  
-   [Control de mensajes y asignación](../mfc/message-handling-and-mapping.md)  
  
-   [CObject, la clase base de la raíz de MFC](../mfc/using-cobject.md)  
  
-   [Arquitectura documento\/vista](../mfc/document-view-architecture.md)  
  
-   [Cuadros de diálogo](../mfc/dialog-boxes.md)  
  
-   [Controles](../mfc/controls-mfc.md)  
  
-   [Barras de controles](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Administración de la memoria](../mfc/memory-management.md)  
  
     Además de proporcionar una ventaja en aplicaciones de escritura para el sistema operativo Windows, MFC también facilita escribir aplicaciones que utilizan específicamente OLE que vincula y que inserta tecnología.  Puede crear la aplicación un contenedor visual OLE de edición, un servidor visual OLE de edición, o ambos, y puede agregar automatización para que otras aplicaciones pueden utilizar objetos de la aplicación o incluso controlarlos remotamente.  
  
-   [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)  
  
     El kit de desarrollo \(CDK\) de controles activex ahora se integra totalmente con el marco.  Fuentes de esta familia de caso información general sobre el desarrollo de controles ActiveX con MFC. \(Controles ActiveX eran anteriormente conocido como controles OLE\).  
  
-   [Programación de la base de datos](../data/data-access-programming-mfc-atl.md)  
  
     MFC también proporciona dos conjuntos de clases de base de datos que simplifican aplicaciones de acceso a los datos.  Mediante las clases de base de datos ODBC, puede conectarse a bases de datos a través de un controlador de ODBC, seleccione los registros de las tablas, y la información de registro de la presentación en un formulario en pantalla.  Mediante las clases de \(DAO\) del Objeto de acceso a datos, puede trabajar con bases de datos con orígenes de datos del motor de base de datos Microsoft Jet o externo \(no JET\), incluidos los orígenes de datos ODBC.  
  
     Además, MFC están totalmente habilitados para escribir aplicaciones que utilizan Unicode y los juegos de caracteres multibyte \(MBCS\), específicamente los juegos de caracteres de doble byte \(DBCS\).  
  
 Para una guía general a la documentación de MFC, vea [Temas generales de MFC](../mfc/general-mfc-topics.md).  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)