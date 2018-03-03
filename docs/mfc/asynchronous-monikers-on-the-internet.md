---
title: "Monikers asincrónicos en Internet | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd7b6be66c3049c1d82aa549cf362a840fd6f265
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="asynchronous-monikers-on-the-internet"></a>Monikers asincrónicos en Internet
Internet requiere nuevos enfoques para el diseño de la aplicación debido a su acceso de red lenta. Las aplicaciones deben realizar de forma asincrónica para evitar la demora de la interfaz de usuario acceso a la red. La clase MFC [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) proporciona compatibilidad asincrónica para descargar archivos.  
  
 Con monikers asincrónicos, puede ampliar la aplicación COM para descargar de forma asincrónica a través de Internet y para proporcionar una representación progresiva de objetos grandes como mapas de bits y VRML. Monikers asincrónicos permiten una propiedad de control ActiveX o un archivo en Internet para su descarga sin bloquear la respuesta de la interfaz de usuario.  
  
## <a name="advantages-of-asynchronous-monikers"></a>Ventajas de los Monikers asincrónicos  
 Puede utilizar los monikers asincrónicos para:  
  
-   Descargar archivos de código y sin bloqueos.  
  
-   Descargar propiedades de controles ActiveX sin bloqueos.  
  
-   Recibir notificaciones de progreso de descarga.  
  
-   Realizar un seguimiento del progreso y la información de estado listo.  
  
-   Proporcionar información de estado al usuario sobre el progreso.  
  
-   Permitir que el usuario pueda cancelar una descarga en cualquier momento.  
  
## <a name="mfc-classes-for-asynchronous-monikers"></a>Clases de MFC para Monikers asincrónicos  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) se deriva de [CMonikerFile](../mfc/reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](../mfc/reference/colestreamfile-class.md). A `COleStreamFile` objeto que representa un flujo de datos; un `CMonikerFile` de objeto usa un `IMoniker` para obtener los datos y un `CAsyncMonikerFile` objeto ello de forma asincrónica.  
  
 Monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario que siga respondiendo durante las transferencias de archivos. Un buen ejemplo de esto es el uso de [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para controles ActiveX.  
  
## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Clases de MFC para las rutas de acceso de datos en controles ActiveX  
 Las clases MFC `CDataPathProperty` y [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implementar propiedades de controles ActiveX que se pueden cargar de forma asincrónica. Propiedades asincrónicas se cargan después de un inicio sincrónico. Los controles ActiveX asincrónicos invocan repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante un proceso de intercambio de propiedad largo.  
  
 La clase `CDataPathProperty` se deriva de la clase `CAsyncMonikerFile`. La clase `CCachedDataPathProperty` se deriva de la clase `CDataPathProperty`. Para implementar propiedades asincrónicas en los controles de ActiveX, derive una clase de `CDataPathProperty` o `CCachedDataPathProperty`e invalidar [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) y otras notificaciones que se va a recibir.  
  
#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Para descargar un archivo mediante monikers asincrónicos  
  
1.  Declarar una clase derivada de [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
2.  Invalidar [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) para mostrar los datos.  
  
3.  Reemplazar otras funciones miembro, incluidos los [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), y [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).  
  
4.  Declare una instancia de esta clase y utilizarla para abrir direcciones URL.  
  
 Para obtener información acerca de cómo descargar de forma asincrónica en un control ActiveX, vea [controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

