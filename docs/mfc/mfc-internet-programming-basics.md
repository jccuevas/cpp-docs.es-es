---
title: Fundamentos de programación para Internet de MFC
ms.date: 11/19/2018
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
ms.openlocfilehash: 3265bffb393eeff1d8a04a41357e2b138aa0ebf7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615573"
---
# <a name="mfc-internet-programming-basics"></a>Fundamentos de programación para Internet de MFC

Microsoft proporciona muchas API para programar aplicaciones de cliente y de servidor. Muchas aplicaciones nuevas se están escribiendo para Internet y, a medida que cambian las tecnologías, las capacidades del explorador y las opciones de seguridad, se escribirán nuevos tipos de aplicaciones. Los exploradores se ejecutan en equipos cliente, lo que proporciona acceso a los World Wide Web y muestra páginas HTML que contienen texto, gráficos, controles ActiveX y documentos. Los servidores proporcionan servicios FTP, HTTP y Gopher, y ejecutan aplicaciones de extensión de servidor mediante CGI. La aplicación personalizada puede recuperar información y proporcionar datos en Internet.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información, vea [controles ActiveX](activex-controls.md).

![Aplicaciones cliente y servidor](../mfc/media/vc38bq1.gif "Aplicaciones cliente y servidor")

MFC proporciona clases que admiten la programación en Internet. Puede usar [COleControl](reference/colecontrol-class.md) y [CDocObjectServer](reference/cdocobjectserver-class.md) y las clases MFC relacionadas para escribir controles ActiveX y documentos activos. Puede usar clases MFC como [CInternetSession](reference/cinternetsession-class.md), [CFtpConnection](reference/cftpconnection-class.md)y [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) para recuperar archivos e información mediante protocolos de Internet como FTP, http y Gopher.

## <a name="in-this-section"></a>En esta sección

- [Clases de MFC relacionadas con Internet](internet-related-mfc-classes.md)

- [Información de Internet por tema](internet-information-by-topic.md)

- [Información de Internet por tarea](internet-information-by-task.md)

- [Tecnología activa en Internet](active-technology-on-the-internet.md)

- [Fundamentos de WinInet](wininet-basics.md)

- [Conceptos básicos de HTML](html-basics.md)

## <a name="related-sections"></a>Secciones relacionadas

- [Controles ActiveX en Internet](activex-controls-on-the-internet.md)

- [Monikers asincrónicos en Internet](asynchronous-monikers-on-the-internet.md)

- [Extensiones de Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)

- [Tareas de programación para Internet de MFC](mfc-internet-programming-tasks.md)

- [Opciones de diseño de aplicaciones](application-design-choices.md)

- [Escritura de aplicaciones MFC](writing-mfc-applications.md)

- [Prueba de aplicaciones para Internet](testing-internet-applications.md)

- [Seguridad de Internet](internet-security-cpp.md)

- [Compatibilidad de ATL con controles DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Sitios web para obtener más información

Para obtener información adicional acerca de la tecnología de Internet de Microsoft, vea el sitio web de [Microsoft Developer Network (MSDN)](https://go.microsoft.com/fwlink/p/?linkid=56322) . (Los vínculos pueden cambiar sin previo aviso).

Este sitio web para desarrolladores contiene información sobre el uso de tecnologías y herramientas de desarrollo de Microsoft, así como historias principales sobre conferencias recientes y futuras. Desde esta página, puede ir a muchos sitios de desarrollador relacionados, incluidos los centros para desarrolladores de .NET y XML. También puede descargar los SDK y los ejemplos de la versión beta.

El [World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) publica especificaciones para HTML, http, CGI y otras tecnologías de World Wide Web.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Más ayuda de Internet

La sección OLE del Windows SDK contiene información adicional sobre la programación OLE. Esta información proporciona detalles sobre el uso de las funciones de Win32 WinInet directamente, en lugar de a través de las clases MFC. También contiene información general sobre las tecnologías de Internet.
