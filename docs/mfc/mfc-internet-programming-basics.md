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
ms.openlocfilehash: 814e63272058200850424e9d5355637111527e1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239140"
---
# <a name="mfc-internet-programming-basics"></a>Fundamentos de programación para Internet de MFC

Microsoft proporciona muchas API para programar aplicaciones de cliente y servidor. Muchas aplicaciones se escriben para Internet y, como las tecnologías, las capacidades del explorador y cambiar las opciones de seguridad, se escribirán los nuevos tipos de aplicaciones. Los exploradores se ejecutan en equipos cliente, que proporciona acceso a World Wide Web y mostrar las páginas HTML que contienen texto, gráficos, controles ActiveX y documentos. Servidores proporcionan servicios gopher, HTTP y FTP y ejecutan aplicaciones de la extensión de servidor mediante CGI. Puede recuperar la información de su aplicación personalizada y se proporcionan datos en Internet.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información, consulte [controles ActiveX](activex-controls.md).

![Las aplicaciones cliente y servidor](../mfc/media/vc38bq1.gif "aplicaciones cliente y servidor")

MFC proporciona clases que admiten la programación de Internet. Puede usar [COleControl](../mfc/reference/colecontrol-class.md) y [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) y relacionados con las clases MFC para crear controles ActiveX y documentos activos. Puede usar las clases MFC como [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md), y [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) para recuperar información mediante protocolos de Internet, como FTP y archivos HTTP y gopher.

## <a name="in-this-section"></a>En esta sección

- [Clases MFC relacionadas con Internet](../mfc/internet-related-mfc-classes.md)

- [Información de Internet por tema](../mfc/internet-information-by-topic.md)

- [Información de Internet por tarea](../mfc/internet-information-by-task.md)

- [Tecnología activa en Internet](../mfc/active-technology-on-the-internet.md)

- [Conceptos básicos de WinInet](../mfc/wininet-basics.md)

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

##  <a name="_core_web_sites_for_more_information"></a> Sitios Web para obtener más información

Para obtener más información acerca de la tecnología de Internet de Microsoft, consulte el [Microsoft Developer Network (MSDN)](http://go.microsoft.com/fwlink/p/?linkid=56322) sitio Web. (Vínculos pueden cambiar sin previo aviso.)

Este sitio Web para desarrolladores contiene información sobre el uso de herramientas de desarrollo de Microsoft y las tecnologías y los artículos principales sobre conferencias recientes y futuros. Desde esta página, puede saltar a muchos sitios para desarrolladores relacionados, incluidos .NET y centros para desarrolladores de XML. También puede descargar los SDK beta y ejemplos.

El [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/p/?linkid=37125) publica especificaciones de HTML, HTTP, CGI y otras tecnologías de World Wide Web.

##  <a name="_core_more_internet_help"></a> Más ayuda de Internet

La sección OLE del SDK de Windows contiene información adicional sobre la programación de OLE. Esta información proporciona detalles sobre cómo usar las funciones de Win32 WinInet directamente, en lugar de a través de las clases MFC. También contiene información general sobre las tecnologías de Internet.
