---
title: "Opciones de dise&#241;o de aplicaciones | Microsoft Docs"
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
  - "diseño de aplicaciones [C++], objetivo del diseño"
  - "diseño de aplicaciones [C++], aplicaciones de Internet"
  - "aplicaciones [MFC], Internet"
  - "aplicaciones cliente [C++], frente a aplicaciones de servidor en Internet"
  - "diseño"
  - "Internet [C++], frente a intranets"
  - "aplicaciones de Internet [C++], diseñar aplicaciones"
  - "aplicaciones de servidor, frente a aplicaciones cliente en Internet"
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Opciones de dise&#241;o de aplicaciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se abordan algunos de los problemas de diseño para tener en cuenta al programar para internet.  
  
 Temas cubiertos en incluyen de caso:  
  
-   [Intranet en internet](#_core_intranet_versus_internet)  
  
-   [Cliente o aplicación de servidor](#_core_client_or_server_application)  
  
-   [La página Web: HTML, documentos activos, Controles ActiveX](#_core_the_web_page.3a_.html.2c_.activex_documents.2c_.activex_controls)  
  
-   [Explorador o aplicación independiente](#_core_browser_or_stand.2d.alone_application)  
  
-   [COM en internet](#_core_com_on_the_internet)  
  
-   [Servicios de descarga de los datos del cliente](#_core_client_data_download_services)  
  
 Si está listo para comenzar la escritura de programa ahora, vea [Aplicaciones MFC de escritura](../mfc/writing-mfc-applications.md).  
  
##  <a name="_core_intranet_versus_internet"></a> Intranet en internet  
 Muchas aplicaciones se ejecutan en internet y son accesibles a los usuarios con un explorador y un acceso a Internet.  Los negocios también están implementando intranets, que son redes profesionales mediante protocolos TCP\/IP y exploradores web.  Intranets proporcionan un origen con facilidad mejorable, central para la información de empresa.  Se pueden utilizar para actualizar el software, porque entregar y tabular limita, para soporte al cliente, y para la entrega de la información.  La tabla siguiente se comparan las características de internet y de intranets.  
  
|Internet|Intranet|  
|--------------|--------------|  
|Ancho banda bajo|Alto ancho banda|  
|Seguridad baja de datos y sistemas|Acceso a datos y sistemas controlados|  
|Control mínimo de contenido|Alto control de contenido|  
  
##  <a name="_core_client_or_server_application"></a> Cliente o aplicación de servidor  
 La aplicación puede ejecutar en un equipo cliente o en un servidor.  La aplicación también se puede almacenar en un servidor, y después descargar a través de Internet y ejecuta en un equipo cliente.  Las clases de MFC WinInet se utilizan para que las aplicaciones cliente podrían descargar archivos.  MFC y las clases del moniker asincrónico se utilizan para descargar los archivos y las propiedades del control.  Clases para los controles y los documentos activos de ActiveX se usan para las aplicaciones cliente y para las aplicaciones que se descargan del servidor para ejecutarse en un cliente.  
  
##  <a name="_core_the_web_page.3a_.html.2c_.activex_documents.2c_.activex_controls"></a> La página Web: HTML, documentos activos, Controles ActiveX  
 Microsoft proporciona varias maneras de proporcionar el contenido de una página Web.  Las páginas Web pueden usar las extensiones HTML estándar o de HTML, como el objeto, para proporcionar contenido dinámico como controles ActiveX.  
  
 De los exploradores web páginas HTML de la pantalla normalmente.  Los documentos activos también pueden mostrar los datos de aplicación en la interfaz simple de establecer y hacer clic de un explorador COM\- habilitado.  El servidor de documentos activos puede mostrar el documento, cuadro completo en el área cliente completa, con sus propios menús y barras de herramientas.  
  
 Los controles ActiveX que escribe se pueden descargar de forma asincrónica de servidor y mostrar en una página Web.  Puede utilizar un lenguaje de script como VBScript para realizar la validación en el cliente antes de enviar información al servidor.  
  
##  <a name="_core_browser_or_stand.2d.alone_application"></a> Explorador o aplicación independiente  
 Puede escribir controles ActiveX que se insertan en los servidores de una página HTML y del documento activo que se ven en un explorador.  Puede escribir páginas HTML que contienen un botón para mostrar una solicitud para ejecutar la aplicación ISAPI en un servidor web.  Puede escribir una aplicación independiente que utilice protocolos de Internet para descargar los archivos y para mostrar información al usuario, sin nunca mediante una aplicación de explorador.  
  
##  <a name="_core_com_on_the_internet"></a> COM en internet  
 Los controles ActiveX, los documentos activos, y los monikeres asincrónicos todos usan tecnologías COM \(modelo de objetos componentes\).  
  
 Los controles ActiveX proporcionan el contenido dinámico a los documentos y las páginas de sitios Internet.  Con COM puede compilar los controles ActiveX y documentos de completo\- cuadro mediante documentos activos.  
  
 Los monikeres asincrónicos proporcionan características para habilitar un control para realizar correctamente en un entorno de internet, incluido un incremental o el progresista significa descargar datos.  Controles también deben funcionar bien con otros controles que pueden recuperar los datos de forma asincrónica al mismo tiempo.  
  
##  <a name="_core_client_data_download_services"></a> Servicios de descarga de los datos del cliente  
 Dos conjuntos de API que ayudarán a transferir datos al cliente son WinInet y monikeres asincrónicos.  Si tiene archivos grandes de .gif y de .avi y controles ActiveX en la página HTML, puede aumentar la capacidad de respuesta al usuario trasladando de forma asincrónica, utilizando monikeres asincrónicos o con WinInet de forma asincrónica.  
  
 Una tarea común en internet está transfiriendo datos.  Si usa ya tecnología activa \(por ejemplo, si tiene un control ActiveX\), puede utilizar monikeres asincrónicos para generar progresivamente los datos cuando éstos se descarga.  Puede utilizar WinInet para transferir datos mediante protocolos de Internet comunes como HTTP, FTP, y gopher.  Ambos métodos proporcionan independencia de protocolo, y proporcionan un nivel abstracto a usar el WinSock y TCP\/IP.  Puede utilizar [WinSock](../mfc/windows-sockets-in-mfc.md) directamente.  
  
 La tabla siguiente se resumen varias maneras de utilizar MFC para transferir datos a través de Internet.  
  
|Utilice este protocolo|En estas condiciones|Mediante estas clases|  
|----------------------------|--------------------------|---------------------------|  
|[Internet que descarga mediante monikeres asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md)|Para las descargas asincrónicas mediante COM, los controles ActiveX, y cualquier protocolo de Internet.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|  
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Para los protocolos de Internet para HTTP, FTP, y gopher.  Los datos se pueden transferir de forma sincrónica o asincrónica y se almacenan en caché sistema\- elevado.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md), y mucho más.|  
|[WinSock](../mfc/windows-sockets-in-mfc.md)|Para aumentar la eficacia y el control máximo.  Entender Requires de sockets y de protocolos TCP\/IP.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)   
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)