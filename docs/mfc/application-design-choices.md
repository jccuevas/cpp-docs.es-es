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
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374628"
---
# <a name="application-design-choices"></a>Opciones de diseño de aplicaciones

En este artículo se describen algunos de los problemas de diseño que se deben tener en cuenta al programar para Internet.

Los temas tratados en este artículo incluyen:

- [Intranet Versus Internet](#_core_intranet_versus_internet)

- [Aplicación de cliente o servidor](#_core_client_or_server_application)

- [La página web](#_core_the_web_page)

- [Navegador o aplicación independiente](#_core_browser_or_standalone)

- [COM en Internet](#_core_com_on_the_internet)

- [Servicios de descarga de datos de clientes](#_core_client_data_download_services)

Si está listo para empezar a escribir el programa ahora, consulte [Escribir aplicaciones MFC](../mfc/writing-mfc-applications.md).

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>Intranet Versus Internet

Muchas aplicaciones se ejecutan en Internet y son accesibles para cualquier persona con un navegador y acceso a Internet. Las empresas también están implementando intranets, que son redes de toda la empresa que utilizan protocolos TCP/IP y exploradores web. Las intranets ofrecen una fuente central fácilmente actualizable para la información de toda la empresa. Se pueden utilizar para actualizar software, para entregar y tabular encuestas, para soporte al cliente y para la entrega de información. En la tabla siguiente se comparan las características de Internet y las intranets.

|Internet|Intranet|
|--------------|--------------|
|Ancho de banda bajo|Ancho de banda elevado|
|Reducción de la seguridad de los datos y sistemas|Acceso controlado a datos y sistemas|
|Control mínimo del contenido|Alto control del contenido|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>Aplicación de cliente o servidor

La aplicación puede ejecutarse en un equipo cliente o en un equipo servidor. La aplicación también se puede almacenar en un servidor y, a continuación, descargar a través de Internet y ejecutar en un equipo cliente. Las clases WinInet de MFC se utilizan para que las aplicaciones cliente descarguen archivos. MFC y clases de moniker asincrónico se utilizan para descargar archivos y propiedades de control. Las clases para controles ActiveX y documentos activos se utilizan para las aplicaciones cliente y para las aplicaciones que se descargan desde el servidor para que se ejecuten en un cliente.

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>La página web: HTML, documentos activos, controles ActiveX

Microsoft ofrece varias formas de proporcionar contenido en una página Web. Las páginas web pueden usar extensiones HTML o HTML estándar, como la etiqueta de objeto, para proporcionar contenido dinámico, como controles ActiveX.

Los exploradores web suelen mostrar páginas HTML. Los documentos activos también pueden mostrar los datos de la aplicación en la sencilla interfaz de apuntar y hacer clic de un explorador habilitado para COM. El servidor de documentos activo puede mostrar el documento, el marco completo en toda el área de cliente, con sus propios menús y barras de herramientas.

Los controles ActiveX que escriba se pueden descargar de forma asincrónica desde el servidor y mostrarse en una página Web. Puede utilizar un lenguaje de scripting como VBScript para realizar la validación del lado cliente antes de enviar información al servidor.

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>Navegador o aplicación independiente

Puede escribir controles ActiveX incrustados en una página HTML y servidores de documentos activos que se ven en un explorador. Puede escribir páginas HTML que contengan un botón para enviar una solicitud para ejecutar la aplicación ISAPI en un servidor Web. Puede escribir una aplicación independiente que utilice protocolos de Internet para descargar archivos y mostrar la información a su usuario, sin usar nunca una aplicación de navegador.

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>COM en Internet

Los controles ActiveX, los documentos activos y los monikers asincrónicos utilizan tecnologías COM (modelo de objetos componentes).

Los controles ActiveX proporcionan contenido dinámico a documentos y páginas en sitios de Internet. Con COM, puede crear controles ActiveX y documentos de marco completo mediante documentos activos.

Los monikers asincrónicos proporcionan características para permitir que un control funcione bien en un entorno de Internet, incluido un medio incremental o progresivo para descargar datos. Los controles también deben funcionar bien con otros controles que también pueden estar recuperando sus datos de forma asincrónica al mismo tiempo.

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>Servicios de descarga de datos de clientes

Dos conjuntos de API que ayudarán a transferir datos a su cliente son WinInet y monikers asincrónicos. Si tiene archivos .gif y .avi grandes y controles ActiveX en la página HTML, puede aumentar la capacidad de respuesta del usuario mediante la descarga asincrónica, ya sea mediante monikers asincrónicos o WinInet de forma asincrónica.

Una tarea común en Internet es la transferencia de datos. Si ya está utilizando la tecnología Active (por ejemplo, si tiene un control ActiveX), puede usar monikers asincrónicos para representar progresivamente los datos a medida que se descargan. Puede utilizar WinInet para transferir datos mediante protocolos de Internet comunes como HTTP, FTP y gopher. Ambos métodos proporcionan independencia de protocolo y proporcionan una capa abstracta para usar WinSock y TCP/IP. Todavía puede utilizar [WinSock](../mfc/windows-sockets-in-mfc.md) directamente.

En la tabla siguiente se resumen varias formas de usar MFC para transferir datos a través de Internet.

|Utilice este protocolo|En estas condiciones|Uso de estas clases|
|-----------------------|----------------------------|-------------------------|
|[Descarga de Internet con monikers asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md)|Para la transferencia asincrónica mediante COM, controles ActiveX y cualquier protocolo de Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Para protocolos de Internet para HTTP, FTP y gopher. Los datos se pueden transferir de forma sincrónica o asincrónica y se almacenan en una memoria caché de todo el sistema.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)y muchos más.|
|[Winsock](../mfc/windows-sockets-in-mfc.md)|Para una máxima eficiencia y control. Requiere comprensión de sockets y protocolos TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Consulte también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación de Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)
