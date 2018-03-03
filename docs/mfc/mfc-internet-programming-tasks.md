---
title: "Tareas de programación de Internet MFC | Documentos de Microsoft"
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
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd726860e181eb352d7368f31a31d2cbd7489000
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-internet-programming-tasks"></a>Tareas de programación para Internet de MFC
Esta sección contiene instrucciones detalladas para agregar compatibilidad con Internet a las aplicaciones. Temas incluyen cómo utilizar las clases MFC para habilitar Internet para las aplicaciones existentes y cómo agregar compatibilidad con documentos activos a un componente COM existente. ¿Desea crear un documento con cotizaciones actualizados al minuto, puntuaciones de fútbol de Pittsburgh, y la temperatura más reciente de Microsoft Antártida proporciona una serie de tecnologías que le permitirán hacerlo a través de Internet.  
  
 Tecnologías activas incluyen los controles ActiveX (antes controles OLE) y documentos activos; WinInet para recuperar fácilmente y guardar archivos a través de Internet; y monikers asincrónicos para la descarga de datos eficaz. Visual C++ proporciona asistentes que le ayudarán a empezar a trabajar rápidamente con una aplicación de inicio. Para obtener una introducción a estas tecnologías, consulte [conceptos básicos de programación de Internet de MFC](../mfc/mfc-internet-programming-basics.md) y [COM en MFC](../mfc/mfc-com.md).  
  
 Tiene siempre deseados a un archivo de FTP, pero aún no lo ha aprendido WinSock y programación de las clases WinInet de protocolos de red encapsular estos protocolos, proporcionándole un sencillo conjunto de funciones que puede utilizar para escribir una aplicación cliente en Internet para descargar archivos uso de HTTP, FTP y gopher. Puede utilizar WinInet para buscar directorios en el disco duro o todo el mundo. Forma transparente puede recopilar datos de varios tipos y lo presenta al usuario en una interfaz integrada.  
  
 ¿Tiene grandes cantidades de datos que se va a descargar asincrónica monikers proporcionan una solución de COM (Component Object Model) para la representación progresiva de objetos grandes. También puede utilizarse WinInet de forma asincrónica.  
  
 La tabla siguiente describen algunas de las cosas que puede hacer con estas tecnologías.  
  
|Tiene|Desea|Debe|  
|--------------|-----------------|----------------|  
|Un servidor Web.|Realizar un seguimiento de los inicios de sesión e información detallada sobre las solicitudes URL.|Escribir un filtro, solicitar notificaciones de eventos de inicio de sesión y asignación de dirección URL.|  
|Un explorador Web.|Proporcionar contenido dinámico.|Crear controles ActiveX y documentos activos.|  
|Una aplicación basada en el documento.|Agregar compatibilidad para un archivo FTP.|Utilizar WinInet o monikers asincrónicos.|  
  
 Vea los temas siguientes para obtener más información para ayudarle a comenzar:  
  
-   [Opciones de diseño de aplicaciones](../mfc/application-design-choices.md)  
  
-   [Escritura de aplicaciones MFC](../mfc/writing-mfc-applications.md)  
  
-   [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)  
  
-   [Actualización de un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md)  
  
-   [Documentos activos en Internet](../mfc/active-documents-on-the-internet.md)  
  
-   [Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [Prueba de aplicaciones para Internet](../mfc/testing-internet-applications.md)  
  
-   [Seguridad de Internet](../mfc/internet-security-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de programación de Internet MFC](../mfc/mfc-internet-programming-basics.md)   
 [Información de Internet por tarea](../mfc/internet-information-by-task.md)

