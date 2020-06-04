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
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366287"
---
# <a name="mfc-internet-programming-basics"></a>Fundamentos de programación para Internet de MFC

Microsoft proporciona muchas API para programar aplicaciones cliente y servidor. Muchas aplicaciones nuevas se están escribiendo para Internet, y a medida que cambien las tecnologías, las capacidades del navegador y las opciones de seguridad, se escribirán nuevos tipos de aplicaciones. Los exploradores se ejecutan en equipos cliente, proporcionan acceso a la World Wide Web y muestran páginas HTML que contienen texto, gráficos, controles ActiveX y documentos. Los servidores proporcionan servicios FTP, HTTP y gopher, y ejecutan aplicaciones de extensión de servidor mediante CGI. La aplicación personalizada puede recuperar información y proporcionar datos en Internet.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información, consulte [Controles ActiveX](activex-controls.md).

![Aplicaciones de cliente y servidor](../mfc/media/vc38bq1.gif "Aplicaciones cliente y servidor")

MFC proporciona clases que admiten la programación de Internet. Puede usar [COleControl](../mfc/reference/colecontrol-class.md) y [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) y clases MFC relacionadas para escribir controles ActiveX y documentos activos. Puede usar clases MFC como [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md)y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) para recuperar archivos e información mediante protocolos de Internet como FTP, HTTP y gopher.

## <a name="in-this-section"></a>En esta sección

- [Clases de MFC relacionadas con Internet](../mfc/internet-related-mfc-classes.md)

- [Información de Internet por tema](../mfc/internet-information-by-topic.md)

- [Información de Internet por tarea](../mfc/internet-information-by-task.md)

- [Tecnología activa en Internet](../mfc/active-technology-on-the-internet.md)

- [Fundamentos de WinInet](../mfc/wininet-basics.md)

- [Conceptos básicos de HTML](../mfc/html-basics.md)

## <a name="related-sections"></a>Secciones relacionadas

- [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)

- [Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)

- [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)

- [Opciones de diseño de aplicaciones](../mfc/application-design-choices.md)

- [Escritura de aplicaciones MFC](../mfc/writing-mfc-applications.md)

- [Prueba de aplicaciones para Internet](../mfc/testing-internet-applications.md)

- [Seguridad de Internet](../mfc/internet-security-cpp.md)

- [Compatibilidad de ATL con controles DHTML](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Sitios web para obtener más información

Para obtener información adicional acerca de la tecnología de Internet de Microsoft, consulte el sitio Web de [Microsoft Developer Network (MSDN).](https://go.microsoft.com/fwlink/p/?linkid=56322) (Los enlaces pueden cambiar sin previo aviso.)

Este sitio web para desarrolladores contiene información sobre el uso de herramientas y tecnologías de desarrollo de Microsoft, e historias principales sobre conferencias recientes y futuras. Desde esta página, puede ir a muchos sitios de desarrolladorrelacionados relacionados, incluidos los Centros de desarrolladores XML y .NET. También puede descargar SDK beta y muestras.

El [World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) publica especificaciones para HTML, HTTP, CGI y otras tecnologías de World Wide Web.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Más ayuda de Internet

La sección OLE del Windows SDK contiene información adicional sobre la programación OLE. Esta información proporciona detalles sobre el uso de las funciones WinInet de Win32 directamente, en lugar de a través de las clases MFC. También contiene información general sobre las tecnologías de Internet.
