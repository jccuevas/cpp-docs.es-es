---
title: Conceptos básicos de programación de Internet MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6896daddc0eb900f9e2a29497eb2dd8a1dc78446
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="mfc-internet-programming-basics"></a>Fundamentos de programación para Internet de MFC
Microsoft proporciona muchas API para programar aplicaciones de cliente y servidor. Se están escribiendo muchas nuevas aplicaciones para Internet y, como las tecnologías, las funciones del explorador y cambio de opciones de seguridad, se escribirán los nuevos tipos de aplicaciones. Los exploradores que se ejecutan en equipos cliente, que proporciona acceso a World Wide Web y mostrar páginas HTML que contienen texto, gráficos, controles ActiveX y documentos. Servidores proporcionan FTP, HTTP y servicios gopher y ejecutan aplicaciones CGI que usan las aplicaciones de extensión de servidor. Su aplicación personalizada puede recuperar la información y proporcionar datos en Internet.  
  
 ![Las aplicaciones cliente y servidor](../mfc/media/vc38bq1.gif "vc38bq1")  
  
 MFC proporciona clases que admiten la programación para Internet. Puede usar [COleControl](../mfc/reference/colecontrol-class.md) y [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) y las clases MFC para crear controles ActiveX y documentos activos relacionadas. Puede usar las clases MFC como [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md), y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) para recuperar archivos y la información mediante protocolos de Internet como FTP, HTTP y gopher.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Clases MFC relacionadas con Internet](../mfc/internet-related-mfc-classes.md)  
  
-   [Información de Internet por tema](../mfc/internet-information-by-topic.md)  
  
-   [Información de Internet por tarea](../mfc/internet-information-by-task.md)  
  
-   [Tecnología activa en Internet](../mfc/active-technology-on-the-internet.md)  
  
-   [Conceptos básicos de WinInet](../mfc/wininet-basics.md)  
  
-   [Conceptos básicos de HTML](../mfc/html-basics.md)  
  
## <a name="related-sections"></a>Secciones relacionadas  
  
-   [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)  
  
-   [Documentos activos en Internet](../mfc/active-documents-on-the-internet.md)  
  
-   [Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)  
  
-   [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)  
  
-   [Opciones de diseño de aplicaciones](../mfc/application-design-choices.md)  
  
-   [Escritura de aplicaciones MFC](../mfc/writing-mfc-applications.md)  
  
-   [Prueba de aplicaciones para Internet](../mfc/testing-internet-applications.md)  
  
-   [Seguridad de Internet](../mfc/internet-security-cpp.md)  
  
-   [Compatibilidad de ATL con controles DHTML](../atl/atl-support-for-dhtml-controls.md)  
  
##  <a name="_core_web_sites_for_more_information"></a> Sitios Web para obtener más información  
 Para obtener información adicional acerca de la tecnología de Microsoft Internet, consulte el [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) sitio Web. (Vínculos pueden cambiar sin previo aviso).  
  
 Este sitio Web para desarrolladores contiene información sobre el uso de herramientas de desarrollo de Microsoft y las tecnologías y artículos principales sobre conferencias recientes y futuras. Desde esta página, puede saltar a muchos de los sitios de desarrollador relacionados, incluidos los .NET y centros de desarrolladores de XML. También puede descargar los SDK beta y ejemplos.  
  
 El [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125) publica especificaciones de HTML, HTTP, CGI y otras tecnologías de World Wide Web.  
  
##  <a name="_core_more_internet_help"></a> Más ayuda de Internet  
 La sección OLE del SDK de Windows contiene información adicional sobre la programación de OLE. Esta información proporciona detalles sobre el uso de las funciones de Win32 WinInet directamente, en lugar de a través de las clases MFC. También contiene información general acerca de las tecnologías de Internet.  
  
## <a name="see-also"></a>Vea también  



