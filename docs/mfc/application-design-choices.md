---
title: "Opciones de diseño de aplicaciones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b78c4c086b40f786d86411c99279245704a48a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="application-design-choices"></a>Opciones de diseño de aplicaciones
En este artículo se describe algunos de los problemas de diseño para tener en cuenta al programar para Internet.  
  
 Los temas tratados en este artículo son:  
  
-   [Intranet e Internet](#_core_intranet_versus_internet)  
  
-   [Aplicación de cliente o servidor](#_core_client_or_server_application)  
  
-   [](#_core_the_web_page)  
  
-   [Explorador o aplicación independiente](#_core_browser_or_standalone)  
  
-   [COM en Internet](#_core_com_on_the_internet)  
  
-   [Servicios de descarga de datos de cliente](#_core_client_data_download_services)  
  
 Si está listo para empezar a escribir su programa ahora, consulte [escribir aplicaciones MFC](../mfc/writing-mfc-applications.md).  
  
##  <a name="_core_intranet_versus_internet"></a>Intranet e Internet  
 Muchas aplicaciones se ejecutan en Internet y son accesibles para cualquier persona con un explorador y el acceso a Internet. Las empresas también implementan intranets, que son redes de toda la empresa mediante los protocolos TCP/IP y exploradores Web. Intranets a menudo ofrecen un origen central, puede actualizar fácilmente para obtener información de toda la empresa. Se puede usar para la actualización de software, para entregar y Tabulando encuestas, de soporte al cliente y para la entrega de información. En la tabla siguiente compara las características de Internet e intranets.  
  
|Internet|Intranet|  
|--------------|--------------|  
|Ancho de banda bajo|Ancho de banda alto|  
|Seguridad reducida de datos y sistemas|Acceso controlado a los datos y sistemas|  
|Control mínimo del contenido|Alto control de contenido|  
  
##  <a name="_core_client_or_server_application"></a>Aplicación de cliente o servidor  
 Puede ejecutar la aplicación en un equipo cliente o en un equipo servidor. La aplicación también se puede almacenar en un servidor y, a continuación, descargar a través de Internet y ejecutar en un equipo cliente. Clases WinInet de MFC se utilizan para las aplicaciones cliente para descargar archivos. MFC y las clases de moniker asincrónico se utilizan para descargar archivos y controlar las propiedades. Clases de controles ActiveX y documentos activos se utilizan para las aplicaciones cliente y para las aplicaciones que se descargan desde el servidor para ejecutarse en un cliente.  
  
##  <a name="_core_the_web_page"></a>La página Web: Controles ActiveX HTML, documentos activos,  
 Microsoft ofrece varias maneras de proporcionar contenido en una página Web. Puede usar páginas Web estándar HTML o HTML extensiones, como la etiqueta object, para proporcionar contenido dinámico como controles ActiveX.  
  
 Los exploradores Web suelen mostrar páginas HTML. Documentos activos también pueden mostrar los datos de aplicación en la interfaz de señalar y hacer clic simple de un explorador compatible con COM. El servidor de documento activo puede mostrar el documento, el marco completo en el área de clientes en su totalidad, con sus propios menús y barras de herramientas.  
  
 Controles ActiveX que cree se pueden descargar de forma asincrónica desde el servidor y mostrar en una página Web. Puede usar un lenguaje de scripting como VBScript para realizar la validación del lado cliente antes de enviar información al servidor.  
  
##  <a name="_core_browser_or_standalone"></a>Explorador o aplicación independiente  
 Puede escribir controles ActiveX que están incrustados en una página HTML y servidores de documentos activos que se ven en un explorador. Puede escribir páginas HTML que contengan un botón para enviar una solicitud para ejecutar la aplicación ISAPI en un servidor Web. Puede escribir una aplicación independiente que usa los protocolos de Internet para descargar archivos y mostrar la información al usuario, sin necesidad de utilizar una aplicación de explorador.  
  
##  <a name="_core_com_on_the_internet"></a>COM en Internet  
 Controles ActiveX, documentos activos y los monikers asincrónicos utilizan tecnologías COM (Component Object Model).  
  
 Controles ActiveX proporcionan contenido dinámico a los documentos y páginas en sitios de Internet. Con COM pueden crear controles ActiveX y documentos de marco completo mediante documentos activos.  
  
 Monikers asincrónicos proporcionan características que permiten un control funcionar bien en un entorno de Internet, incluido un incremental o significa progresivo para descargar datos. Controles también deben funcionar bien con otros controles que también puedan estar recuperando sus datos de forma asincrónica al mismo tiempo.  
  
##  <a name="_core_client_data_download_services"></a>Servicios de descarga de datos de cliente  
 Dos conjuntos de API que le ayudará a transferir datos a su cliente son WinInet y monikers asincrónicos. Si tiene grandes .gif y archivos .avi y controles ActiveX en la página HTML, puede aumentar la capacidad de respuesta al usuario mediante la descarga de forma asincrónica, ya sea mediante monikers asincrónicos o usando WinInet de forma asincrónica.  
  
 Una tarea común en Internet es transferir los datos. Si ya usa tecnología activa (por ejemplo, si tiene un control ActiveX), puede utilizar monikers asincrónicos para representar progresivamente los datos tal y como se descarga. Puede utilizar WinInet para transferir datos mediante protocolos comunes de Internet como HTTP, FTP y gopher. Ambos métodos proporcionan independencia del protocolo y una capa abstracta para la utilización de WinSock y TCP/IP. Todavía puede usar [WinSock](../mfc/windows-sockets-in-mfc.md) directamente.  
  
 En la tabla siguiente resume las diferentes formas de utilizar MFC para transferir datos a través de Internet.  
  
|Utilice este protocolo|En estas condiciones|Mediante estas clases|  
|-----------------------|----------------------------|-------------------------|  
|[Internet descargar uso de Monikers asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md)|Para la transferencia asincrónica mediante COM, controles ActiveX y cualquier protocolo de Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Para los protocolos de Internet para HTTP, FTP y gopher. Datos se pueden transferir de forma sincrónica o asincrónica y se almacenan en una caché de todo el sistema.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)y mucho más.|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Para obtener la máxima eficacia y control. Requiere conocimientos de los sockets y protocolos TCP/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Conceptos básicos de programación de Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)

