---
title: Tareas de programación para Internet de MFC
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
ms.openlocfilehash: 1b0a8696e25054099cdbf208dd5a1f713bfbe6d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164961"
---
# <a name="mfc-internet-programming-tasks"></a>Tareas de programación para Internet de MFC

Esta sección contiene instrucciones detalladas para agregar compatibilidad con Internet a las aplicaciones. Los temas incluyen cómo usar las clases MFC para habilitar Internet para las aplicaciones existentes y cómo agregar compatibilidad con documentos activos a un componente COM existente. ¿Desea crear un documento con cotizaciones de bolsa actualizados al minuto, las puntuaciones de fútbol de Pittsburgh, y la temperatura actual en la Antártida Microsoft proporciona una serie de tecnologías que le ayudarán a hacerlo a través de Internet.

Tecnologías activas incluyen los controles ActiveX (antes controles OLE) y documentos activos; WinInet para recuperar fácilmente y guardar archivos a través de Internet; y monikers asincrónicos para la descarga de datos eficaz. Visual C++ proporciona asistentes que le ayudarán a empezar a trabajar rápidamente con una aplicación de inicio. Para obtener una introducción a estas tecnologías, consulte [Fundamentos de programación de Internet de MFC](../mfc/mfc-internet-programming-basics.md) y [COM en MFC](../mfc/mfc-com.md).

Deseado siempre a un archivo de FTP, pero aún no lo ha aprendido WinSock y programación de las clases WinInet de protocolos de red encapsular estos protocolos, proporcionándole un sencillo conjunto de funciones que puede usar para escribir una aplicación cliente en Internet para descargar archivos uso de HTTP, FTP y gopher. Puede usar WinInet para buscar directorios en el disco duro o en todo el mundo. Transparente, puede recopilar datos de varios tipos diferentes y presentarlos al usuario en una interfaz integrada.

¿Tiene grandes cantidades de datos que se va a descargar asincrónico monikers proporcionan una solución de COM (Component Object Model) para la representación progresiva de objetos grandes. También puede utilizarse WinInet de forma asincrónica.

En la tabla siguiente se describe algunas de las cosas que puede hacer con estas tecnologías.

|Tiene|Desea|Debe|
|--------------|-----------------|----------------|
|Un servidor Web.|Realizar un seguimiento de los inicios de sesión y obtener información detallada acerca de las solicitudes URL.|Escribir un filtro, solicitar notificaciones de eventos de inicio de sesión y la asignación de dirección URL.|
|Un explorador Web.|Proporcionar contenido dinámico.|Crear controles ActiveX y documentos activos.|
|Una aplicación basada en el documento.|Agregar compatibilidad con FTP un archivo.|Usar WinInet o monikers asincrónicos.|

Vea los temas siguientes para obtener más información comenzar:

- [Opciones de diseño de aplicaciones](../mfc/application-design-choices.md)

- [Escritura de aplicaciones MFC](../mfc/writing-mfc-applications.md)

- [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)

- [Actualización de un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md)

- [Monikers asincrónicos en Internet](../mfc/asynchronous-monikers-on-the-internet.md)

- [Prueba de aplicaciones para Internet](../mfc/testing-internet-applications.md)

- [Seguridad de Internet](../mfc/internet-security-cpp.md)

## <a name="see-also"></a>Vea también

[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Información de Internet por tarea](../mfc/internet-information-by-task.md)
