---
title: "Monikers asincr&#243;nicos en Internet | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "controles ActiveX [C++], asincrónico"
  - "monikers asincrónicos [C++]"
  - "descargar recursos de Internet y monikers asincrónicos"
  - "Internet [C++], descargas asincrónicas"
  - "MFC [C++], monikers asincrónicos"
  - "optimización [C++], descargas asincrónicas a través de Internet"
  - "aplicaciones web [C++], asincrónico"
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Monikers asincr&#243;nicos en Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Internet requiere nuevos métodos al diseño de aplicaciones debido al acceso de red lenta.  Las aplicaciones deben realizar el acceso de red de forma asincrónica para evitar atascar la interfaz de usuario.  La clase [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) MFC proporciona compatibilidad asincrónico para descargar archivos.  
  
 Con monikeres asincrónicos, puede extender la aplicación COM para descargar de forma asincrónica a través de Internet y proporcionar la representación progresiva de objetos grandes como mapas de bits y objetos de VRML.  Los monikeres asincrónicos permiten una propiedad de control ActiveX o un archivo en internet que se descargará sin bloquear la respuesta de la interfaz de usuario.  
  
## Ventajas de monikeres asincrónicos  
 Puede utilizar monikeres asincrónicos:  
  
-   Código y archivos de descarga sin bloquearse.  
  
-   Propiedades de descarga en los controles ActiveX sin bloquearse.  
  
-   Reciba las notificaciones de progreso de transferencia.  
  
-   Realizar el seguimiento del progreso y la información del estado listo.  
  
-   Proporciona información de estado al usuario sobre el progreso.  
  
-   Permite al usuario cancelar una descarga en cualquier momento.  
  
## Clases de MFC para los monikeres asincrónicos  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) se deriva de [CMonikerFile](../mfc/reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](../mfc/reference/colestreamfile-class.md).  Un objeto de `COleStreamFile` representa una secuencia de datos; un objeto de `CMonikerFile` utiliza `IMoniker` para obtener los datos, y un objeto de `CAsyncMonikerFile` lo hace de forma asincrónica.  
  
 Los monikeres asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario rápida durante las transferencias de archivos.  Un ejemplo típico de esto es el uso de [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) de proporcionar las propiedades asincrónicas para controles ActiveX.  
  
## Clases MFC para las rutas de datos en Controles ActiveX  
 Las clases MFC `CDataPathProperty` y [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implementan las propiedades del control ActiveX que se pueden cargar de forma asincrónica.  Las propiedades asincrónicas se cargan después del lanzamiento sincrónico.  Los controles ActiveX asincrónicos se invoca repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante un proceso largo de intercambio de propiedad.  
  
 `CDataPathProperty` se deriva de `CAsyncMonikerFile`.  `CCachedDataPathProperty` se deriva de `CDataPathProperty`.  Para implementar propiedades asincrónicas en los controles ActiveX, derive una clase de `CDataPathProperty` o de `CCachedDataPathProperty`, y reemplazar [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) y otras notificaciones que desea recibir.  
  
#### Para descargar un archivo mediante monikeres asincrónicos  
  
1.  Declare una clase derivada de [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
2.  Reemplazo [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) para mostrar los datos.  
  
3.  Invalide otras funciones miembro, incluidos [OnProgress](../Topic/CAsyncMonikerFile::OnProgress.md), [OnStartBinding](../Topic/CAsyncMonikerFile::OnStartBinding.md), y [OnStopBinding](../Topic/CAsyncMonikerFile::OnStopBinding.md).  
  
4.  Declare una instancia de esta clase y utilizarla para abrir las direcciones URL.  
  
 Para obtener información sobre la descarga de forma asincrónica en un control ActiveX, vea [Controles ActiveX en internet](../mfc/activex-controls-on-the-internet.md).  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)