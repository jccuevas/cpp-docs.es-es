---
title: Opciones de diseño de aplicaciones
ms.date: 11/04/2016
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
ms.openlocfilehash: cdb294e4ab808a7e4cbcec457f6e744eff9f12cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394668"
---
# <a name="application-design-choices"></a>Opciones de diseño de aplicaciones

Este artículo describen algunos de los problemas de diseño a tener en cuenta al programar para Internet.

Los temas tratados en este artículo incluyen:

- [Intranet Versus Internet](#_core_intranet_versus_internet)

- [Aplicación de servidor o cliente](#_core_client_or_server_application)

- [](#_core_the_web_page)

- [Explorador o aplicación independiente](#_core_browser_or_standalone)

- [COM en Internet](#_core_com_on_the_internet)

- [Servicios de descarga de datos de cliente](#_core_client_data_download_services)

Si está listo para empezar a escribir el programa ahora, consulte [escribir aplicaciones MFC](../mfc/writing-mfc-applications.md).

##  <a name="_core_intranet_versus_internet"></a> Intranet Versus Internet

Muchas aplicaciones se ejecutan en Internet y son accesibles para cualquier persona con un explorador y el acceso a Internet. Las empresas también implementan intranets, que son redes corporativas mediante los protocolos TCP/IP y exploradores Web. Las intranets ofrecen un origen central, puede actualizar fácilmente para obtener información en toda la empresa. Se puede usar para la actualización de software, para entregar y forma que contabilice encuestas, soporte técnico del cliente y para la entrega de información. La tabla siguiente comparan las características de Internet e intranets.

|Internet|Intranet|
|--------------|--------------|
|Ancho de banda bajo|Ancho de banda alto|
|Reducir la seguridad de datos y sistemas|Acceso controlado a los datos y sistemas|
|Control mínimo del contenido|Alto control de contenido|

##  <a name="_core_client_or_server_application"></a> Aplicación de servidor o cliente

Puede ejecutar la aplicación en un equipo cliente o en un equipo servidor. La aplicación es posible que también se almacenan en un servidor y, a continuación, descargaran por Internet y ejecutar en un equipo cliente. Clases WinInet de MFC se utilizan para las aplicaciones cliente para descargar archivos. MFC y las clases moniker asincrónico se usan para descargar archivos y propiedades del control. Las clases de controles ActiveX y documentos activos se usan para las aplicaciones cliente y para las aplicaciones que se descargan desde el servidor para ejecutarse en un cliente.

##  <a name="_core_the_web_page"></a> La página Web: Controles ActiveX HTML, los documentos activos

Microsoft ofrece varias maneras de proporcionar contenido en una página Web. Puede usar las páginas Web HTML estándar o HTML extensiones, como la etiqueta de objeto, para proporcionar contenido dinámico como controles ActiveX.

Los exploradores Web suelen mostrar páginas HTML. Documentos activos también pueden mostrar datos de la aplicación en la interfaz de apuntar y hacer clic simple de un explorador compatible con COM. El servidor de documentos activos puede mostrar el documento, el marco completo en el área cliente completa, con sus propios menús y barras de herramientas.

Controles ActiveX que cree se pueden descargar de forma asincrónica desde el servidor y aparece en una página Web. Puede usar un lenguaje de scripting como VBScript para realizar la validación del lado cliente antes de enviar información al servidor.

##  <a name="_core_browser_or_standalone"></a> Explorador o aplicación independiente

Puede escribir controles ActiveX que están incrustados en una página HTML y servidores de documentos activos que se ven en un explorador. Puede escribir páginas HTML que contienen un botón para enviar una solicitud para ejecutar la aplicación ISAPI en un servidor Web. Puede escribir una aplicación independiente que usa protocolos de Internet para descargar archivos y mostrar la información al usuario, sin necesidad de utilizar una aplicación de explorador.

##  <a name="_core_com_on_the_internet"></a> COM en Internet

Controles ActiveX, documentos activos y monikers asincrónicos usan las tecnologías COM (Component Object Model).

Controles ActiveX proporcionan contenido dinámico a los documentos y páginas en sitios de Internet. Con COM puede crear controles ActiveX y documentos de marco completo mediante documentos activos.

Monikers asincrónicos proporcionan características para habilitar un control funcionar bien en un entorno de Internet, incluidas una incremental o significa progresivo para descargar datos. Los controles también deben funcionar bien con otros controles que es posible que también se puede recuperar sus datos asincrónicamente al mismo tiempo.

##  <a name="_core_client_data_download_services"></a> Servicios de descarga de datos de cliente

Dos conjuntos de API que le ayudarán a transferir datos a su cliente son WinInet y monikers asincrónicos. Si tiene grandes .gif y archivos .avi y controles ActiveX en su página HTML, puede aumentar la capacidad de respuesta al usuario mediante la descarga de forma asincrónica, ya sea mediante monikers asincrónicos o usando WinInet de forma asincrónica.

La transferencia de datos es una tarea común en Internet. Si ya usa tecnología activa (por ejemplo, si tiene un control ActiveX), puede usar monikers asincrónicos que represente progresivamente los datos que descarga. Puede usar WinInet para transferir datos mediante los protocolos de Internet comunes como HTTP, FTP y gopher. Ambos métodos proporcionan independencia del protocolo y proporcionan una capa abstracta para usar WinSock y TCP/IP. Todavía puede usar [WinSock](../mfc/windows-sockets-in-mfc.md) directamente.

La tabla siguiente resume las varias formas de usar MFC para transferir datos a través de Internet.

|Utilice este protocolo|En estas condiciones|Uso de estas clases|
|-----------------------|----------------------------|-------------------------|
|[Internet descargar uso de Monikers asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md)|Para la transferencia asincrónica mediante COM, controles ActiveX y cualquier protocolo de Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Para los protocolos de Internet para HTTP, FTP y gopher. Datos se pueden transferir de forma sincrónica o asincrónica y se almacenan en una caché de todo el sistema.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)y mucho más.|
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Para obtener la máxima eficacia y control. Requiere la comprensión de los sockets y protocolos TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Vea también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)
