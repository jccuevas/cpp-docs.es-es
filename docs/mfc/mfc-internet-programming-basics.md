---
title: "Fundamentos de programaci&#243;n para Internet de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "tecnología activa [C++]"
  - "controles ActiveX [C++], Internet"
  - "aplicaciones de Internet [C++]"
  - "aplicaciones de Internet [C++], tecnología activa"
  - "aplicaciones de Internet [C++], controles ActiveX"
  - "aplicaciones de Internet [C++], escribir"
  - "contenido de Internet [C++]"
  - "ISAPI"
  - "extensiones ISAPI, programar con ISAPI"
  - "filtros ISAPI, programar con ISAPI"
  - "programación [C++], Internet"
  - "aplicaciones web [C++], clases MFC"
  - "WinInet (clases)"
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Fundamentos de programaci&#243;n para Internet de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft proporciona muchas API para el cliente programado y las aplicaciones de servidor.  Muchas aplicaciones nuevas se están escribiendo para internet y, como las tecnologías, las capacidades del explorador, y el cambio de las opciones de seguridad, los nuevos tipos de aplicaciones se escriben.  Exploradores se ejecutan en los equipos cliente, proporcionando acceso a World Wide Web y mostrar páginas HTML que contienen texto, gráficos, los controles ActiveX, y documentos.  Los Servidores proporcionan FTP, HTTP, y los servicios de gopher, y las aplicaciones de extensiones de servidor de usar CGI.  La aplicación personalizada puede recuperar información y proporcionar datos en internet.  
  
 ![Aplicaciones cliente y servidor](../mfc/media/vc38bq1.png "vc38BQ1")  
  
 MFC proporciona clases que programación admiten de internet.  Puede utilizar [COleControl](../mfc/reference/colecontrol-class.md) y [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) y las clases MFC relacionadas para escribir controles y documentos activos de ActiveX.  Puede utilizar clases MFC como [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md), y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) para recuperar archivos e información mediante protocolos de Internet como FTP, HTTP, y gopher.  
  
## En esta sección  
  
-   [Clases MFC Herramienta de creación de HTML\-relacionadas](../mfc/internet-related-mfc-classes.md)  
  
-   [Información de Internet por tema](../mfc/internet-information-by-topic.md)  
  
-   [Información de Internet por tarea](../mfc/internet-information-by-task.md)  
  
-   [Tecnología activa en internet](../mfc/active-technology-on-the-internet.md)  
  
-   [Fundamentos de WinInet](../mfc/wininet-basics.md)  
  
-   [fundamentos de HTML](../mfc/html-basics.md)  
  
-   [fundamentos de HTTP](../mfc/http-basics.md)  
  
## Secciones relacionadas  
  
-   [Controles ActiveX en internet](../mfc/activex-controls-on-the-internet.md)  
  
-   [Documentos activos en internet](../mfc/active-documents-on-the-internet.md)  
  
-   [Monikeres asincrónicos en internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Extensiones de Internet para Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [Tareas de programación de Internet de MFC](../mfc/mfc-internet-programming-tasks.md)  
  
-   [Opciones de diseño de aplicaciones](../mfc/application-design-choices.md)  
  
-   [Aplicaciones MFC de escritura](../mfc/writing-mfc-applications.md)  
  
-   [Aplicaciones de internet de pruebas](../mfc/testing-internet-applications.md)  
  
-   [Seguridad de Internet](../mfc/internet-security-cpp.md)  
  
-   [Compatibilidad ATL para Controles de DHTML](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> Sitios Web para la información de Más  
 Para obtener más información sobre la tecnología de Microsoft Internet, vea [Microsoft Developer Network \(MSDN\)](http://go.microsoft.com/fwlink/?LinkID=56322) el sitio Web. \(Los vínculos pueden cambiar sin previo aviso.\)  
  
 Este sitio Web para los desarrolladores contiene información sobre cómo utilizar las herramientas de desarrollo y las tecnologías de Microsoft, y los casos superiores sobre informes recientes y futuras.  En esta página, puede ir a muchos sitios relacionados del desarrollador, incluir .NET, y a centros de desarrollador de XML.  También puede descargar el SDK beta y ejemplos.  
  
 [World Wide Web Consortium \(W3C\)](http://go.microsoft.com/fwlink/?LinkID=37125) Publica las especificaciones de HTML, HTTP, CGI, y otras tecnologías de World Wide Web.  
  
##  <a name="_core_more_internet_help"></a> Más Ayuda de internet  
 La sección OLE de [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] contiene información adicional sobre programación OLE.  Esta información proporciona detalles sobre cómo utilizar las funciones de Win32 WinInet directamente, en lugar de a través de las clases MFC.  También contiene información general sobre tecnologías de internet.  
  
## Vea también  
 [MFC Internet Programming \(NIB\)](http://msdn.microsoft.com/es-es/0f7a1f3a-385b-4d56-a55b-0d766840c58a)