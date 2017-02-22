---
title: "Tareas de programaci&#243;n para Internet de MFC | Microsoft Docs"
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
  - "aplicaciones de Internet, primeros pasos"
  - "aplicaciones de Internet, introducción"
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Tareas de programaci&#243;n para Internet de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta sección contiene los pasos detallados para agregar compatibilidad de internet a las aplicaciones.  Los temas incluyen cómo utilizar la Herramienta de creación de HTML\- permiso de clases MFC las aplicaciones existentes, y cómo agregar compatibilidad del documento activo al componente COM existente.  ¿Desea crear un documento con las puntuaciones de última hora stock quotes, de fútbol de Pittsburgh, y la última temperatura de Antártida?  Microsoft proporciona varias tecnologías para ayudarle hace a través de internet.  
  
 Las tecnologías activo incluyen controles ActiveX \(antes controles OLE\) y los documentos activos; WinInet para fácilmente recuperar y guardar archivos a través de Internet; y monikeres asincrónicos para la transferencia eficaz de los datos.  Visual C\+\+ proporciona asistentes para ayudarle a comenzar rápidamente con una aplicación inicial.  Para obtener una introducción a estas tecnologías, vea [Internet de MFC que programa fundamentos](../mfc/mfc-internet-programming-basics.md) y [MFC COM](../mfc/mfc-com.md).  
  
 ¿Le tienen deseado a FTP un archivo pero no han aprendido siempre protocolos de programación WinSock y red?  Las clases de WinInet encapsulan estos protocolos, proporcionando de es un conjunto simple de funciones que puede utilizar para escribir una aplicación cliente en internet los archivos de descarga mediante HTTP, FTP, y de gopher.  Puede utilizar WinInet para buscar directorios en el disco duro o en todo el mundo.  Puede transparente recopilar datos de varios tipos, y se muestra al usuario en una interfaz integrada.  
  
 ¿Tiene grandes cantidades de datos a descargar?  Los monikeres asincrónicos proporcionan una solución COM \(modelo de objetos componentes\) para la representación progresiva de objetos grandes.  WinInet también se puede utilizar de forma asincrónica.  
  
 La tabla siguiente se describen algunas de las cosas que puede hacer con estas tecnologías.  
  
|Tiene|Desea que|Debe|  
|-----------|---------------|----------|  
|Un servidor web.|Inicios de sesión e información detallada de pista sobre las solicitudes URL.|Escriba un filtro, notificaciones de solicitudes para los eventos de inicio de sesión y la asignación de direcciones URL.|  
|Un explorador web.|Proporcionar el contenido dinámico.|Cree los controles y los documentos activos de ActiveX.|  
|Una aplicación documento\- basada en.|Agregue compatibilidad para FTP un archivo.|Utilice WinInet o los monikeres asincrónicos.|  
  
 Vea los temas siguientes para obtener detalles como punto de partida para:  
  
-   [Opciones de diseño de aplicaciones](../mfc/application-design-choices.md)  
  
-   [Aplicaciones MFC de escritura](../mfc/writing-mfc-applications.md)  
  
-   [Controles ActiveX en internet](../mfc/activex-controls-on-the-internet.md)  
  
-   [Actualizar un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md)  
  
-   [Documentos activos en internet](../mfc/active-documents-on-the-internet.md)  
  
-   [Monikeres asincrónicos en internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Aplicaciones de internet de pruebas](../mfc/testing-internet-applications.md)  
  
-   [Seguridad de Internet](../mfc/internet-security-cpp.md)  
  
## Vea también  
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)   
 [Información de Internet por tarea](../mfc/internet-information-by-task.md)