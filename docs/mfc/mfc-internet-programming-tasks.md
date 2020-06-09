---
title: Tareas de programación para Internet de MFC
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
ms.openlocfilehash: 6d8a542ada94bc52ee2000bc92ae0457ec87609c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617959"
---
# <a name="mfc-internet-programming-tasks"></a>Tareas de programación para Internet de MFC

Esta sección contiene los pasos detallados para agregar compatibilidad con Internet a las aplicaciones. Entre los temas se incluye cómo usar las clases MFC para habilitar las aplicaciones existentes en Internet y cómo agregar compatibilidad con documentos activos al componente COM existente. ¿Desea crear un documento con cotizaciones de bolsa actualizadas, las puntuaciones de fútbol de Pittsburgh y la temperatura más reciente de la Antártida Microsoft proporciona varias tecnologías para ayudarle a hacerlo a través de Internet.

Las tecnologías activas incluyen controles ActiveX (antes controles OLE) y documentos activos; WinInet para recuperar y guardar archivos fácilmente en Internet; y monikers asincrónicos para la descarga eficaz de datos. Visual C++ proporciona asistentes que le ayudarán a empezar a trabajar rápidamente con una aplicación de inicio. Para obtener una introducción a estas tecnologías, vea fundamentos de la [programación para Internet de MFC](mfc-internet-programming-basics.md) y com de [MFC](mfc-com.md).

Tenga siempre que desee enviar por FTP un archivo, pero no ha aprendido WinSock y protocolos de programación de red. las clases WinInet encapsulan estos protocolos, lo que le proporciona un sencillo conjunto de funciones que puede usar para escribir una aplicación cliente en Internet para descargar archivos mediante HTTP, FTP y Gopher. Puede usar WinInet para buscar directorios en el disco duro o en todo el mundo. Puede recopilar de forma transparente datos de varios tipos diferentes y presentarlos al usuario en una interfaz integrada.

Si tiene grandes cantidades de datos para descargar monikers asincrónicos, proporcione una solución COM (modelo de objetos componentes) para la representación progresiva de objetos grandes. WinInet también se puede utilizar de forma asincrónica.

En la tabla siguiente se describen algunas de las cosas que puede hacer con estas tecnologías.

|Tiene|Desea|Debe|
|--------------|-----------------|----------------|
|Un servidor Web.|Realizar un seguimiento de los inicios de sesión e información detallada sobre las solicitudes URL.|Escribir un filtro, solicitar notificaciones para eventos de inicio de sesión y asignación de direcciones URL.|
|Un explorador Web.|Proporcionar contenido dinámico.|Crear controles ActiveX y documentos activos.|
|Una aplicación basada en documento.|Agregar compatibilidad para FTP a un archivo.|Usar los monikers de WinInet o asincrónicos.|

Vea los temas siguientes para obtener más información sobre cómo comenzar:

- [Opciones de diseño de aplicaciones](application-design-choices.md)

- [Escritura de aplicaciones MFC](writing-mfc-applications.md)

- [Controles ActiveX en Internet](activex-controls-on-the-internet.md)

- [Actualizar un control ActiveX existente](upgrading-an-existing-activex-control.md)

- [Monikers asincrónicos en Internet](asynchronous-monikers-on-the-internet.md)

- [Prueba de aplicaciones para Internet](testing-internet-applications.md)

- [Seguridad de Internet](internet-security-cpp.md)

## <a name="see-also"></a>Consulte también

[Fundamentos de la programación para Internet de MFC](mfc-internet-programming-basics.md)<br/>
[Información de Internet por tarea](internet-information-by-task.md)
