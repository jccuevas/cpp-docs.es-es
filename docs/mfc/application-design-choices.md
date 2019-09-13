---
title: Opciones de diseño de aplicaciones
ms.date: 09/12/2019
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
ms.openlocfilehash: b205599ed3bf33e84516120b1855482797b86c9b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924914"
---
# <a name="application-design-choices"></a>Opciones de diseño de aplicaciones

En este artículo se tratan algunos de los problemas de diseño que se deben tener en cuenta al programar para Internet.

Los temas que se tratan en este artículo son:

- [Intranet frente a Internet](#_core_intranet_versus_internet)

- [Aplicación de cliente o de servidor](#_core_client_or_server_application)

- [La página web](#_core_the_web_page)

- [Explorador o aplicación independiente](#_core_browser_or_standalone)

- [COM en Internet](#_core_com_on_the_internet)

- [Servicios de descarga de datos de cliente](#_core_client_data_download_services)

Si está listo para empezar a escribir el programa ahora, consulte [Writing MFC Applications](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a> Intranet Versus Internet

Muchas aplicaciones se ejecutan en Internet y son accesibles para cualquier persona con un explorador y acceso a Internet. Las empresas también implementan intranets, que son redes de toda la empresa que usan protocolos TCP/IP y exploradores Web. Las intranets ofrecen una fuente central y fácil de actualizar para obtener información sobre toda la empresa. Se pueden usar para actualizar el software, para entregar y tabular encuestas, para el soporte al cliente y para la entrega de información. En la tabla siguiente se comparan las características de Internet y las intranets.

|Internet|Intranet|
|--------------|--------------|
|Ancho de banda bajo|Ancho de banda alto|
|Menor seguridad de los datos y sistemas|Acceso controlado a datos y sistemas|
|Control mínimo de contenido|Control alto del contenido|

##  <a name="_core_client_or_server_application"></a>Aplicación de cliente o de servidor

La aplicación puede ejecutarse en un equipo cliente o en un equipo servidor. La aplicación también puede almacenarse en un servidor y descargarse a través de Internet y ejecutarse en un equipo cliente. Las clases WinInet de MFC se utilizan para que las aplicaciones cliente descarguen archivos. Las clases de moniker de MFC y asincrónico se usan para descargar archivos y propiedades de control. Las clases para los controles ActiveX y los documentos activos se usan para las aplicaciones cliente y para las aplicaciones que se descargan del servidor para ejecutarse en un cliente.

##  <a name="_core_the_web_page"></a>La página web: HTML, documentos activos, controles ActiveX

Microsoft ofrece varias formas de proporcionar contenido en una página web. Las páginas web pueden usar extensiones HTML o HTML estándar, como la etiqueta de objeto, para proporcionar contenido dinámico como controles ActiveX.

Los exploradores Web suelen mostrar páginas HTML. Los documentos activos también pueden mostrar los datos de la aplicación en la interfaz simple de apuntar y hacer clic de un explorador habilitado para COM. El servidor de documentos activos puede mostrar el documento, el marco completo en todo el área cliente, con sus propios menús y barras de herramientas.

Los controles ActiveX que escriba se pueden descargar de forma asincrónica desde el servidor y mostrarse en una página web. Puede usar un lenguaje de scripting como VBScript para realizar la validación del lado cliente antes de enviar información al servidor.

##  <a name="_core_browser_or_standalone"></a>Explorador o aplicación independiente

Puede escribir controles ActiveX que están incrustados en una página HTML y servidores de documentos activos que se ven en un explorador. Puede escribir páginas HTML que contengan un botón para enviar una solicitud para ejecutar la aplicación ISAPI en un servidor Web. Puede escribir una aplicación independiente que use protocolos de Internet para descargar archivos y mostrar la información al usuario sin necesidad de usar una aplicación de explorador.

##  <a name="_core_com_on_the_internet"></a>COM en Internet

Los controles ActiveX, los documentos activos y los monikers asincrónicos usan tecnologías COM (modelo de objetos componentes).

Los controles ActiveX proporcionan contenido dinámico a documentos y páginas de sitios de Internet. Con COM, puede compilar controles ActiveX y documentos de marco completo mediante documentos activos.

Los monikers asincrónicos proporcionan características para permitir que un control funcione correctamente en un entorno de Internet, incluido un medio incremental o progresivo para descargar datos. Los controles también deben funcionar bien con otros controles que también pueden estar recuperando sus datos de forma asincrónica al mismo tiempo.

##  <a name="_core_client_data_download_services"></a>Servicios de descarga de datos de cliente

Dos conjuntos de API que le ayudarán a transferir datos al cliente son los monikers de WinInet y asincrónicos. Si tiene archivos. gif y. avi grandes y controles ActiveX en la página HTML, puede aumentar la capacidad de respuesta al usuario mediante la descarga asincrónica, ya sea mediante el uso de monikers asincrónicos o mediante WinInet de forma asincrónica.

Una tarea común en Internet es la transferencia de datos. Si ya usa tecnología activa (por ejemplo, si tiene un control ActiveX), puede usar monikers asincrónicos para representar progresivamente los datos a medida que se descargan. Puede usar WinInet para transferir datos mediante protocolos de Internet comunes como HTTP, FTP y Gopher. Ambos métodos proporcionan independencia del protocolo y proporcionan una capa abstracta para usar WinSock y TCP/IP. Todavía puede usar [Winsock](../mfc/windows-sockets-in-mfc.md) directamente.

En la tabla siguiente se resumen varias formas de usar MFC para transferir datos a través de Internet.

|Usar este protocolo|En estas condiciones|Usar estas clases|
|-----------------------|----------------------------|-------------------------|
|[Descarga de Internet con monikers asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md)|Para transferencias asincrónicas mediante COM, controles ActiveX y cualquier protocolo de Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Para protocolos de Internet para HTTP, FTP y Gopher. Los datos se pueden transferir de forma sincrónica o asincrónica y se almacenan en una caché de todo el sistema.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)y muchos más.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Para obtener la máxima eficacia y control. Requiere la comprensión de los sockets y los protocolos TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Vea también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)
