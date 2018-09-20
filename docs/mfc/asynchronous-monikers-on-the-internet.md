---
title: Monikers asincrónicos en Internet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdb310891cd98e6bf3a8afa0b92cce01e5f5c6ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409911"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Monikers asincrónicos en Internet

Internet requiere nuevos enfoques para el diseño de la aplicación debido a su acceso de red lenta. Las aplicaciones deben realizar de forma asincrónica para evitar el estancamiento la interfaz de usuario acceso a la red. La clase MFC [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) proporciona compatibilidad asincrónica para descargar los archivos.

Con monikers asincrónicos, puede ampliar la aplicación COM para descargar de forma asincrónica a través de Internet y para proporcionar una representación progresiva de objetos grandes como los mapas de bits y VRML. Monikers asincrónicos habilitan una propiedad de control ActiveX o un archivo en Internet para su descarga sin bloquear la respuesta de la interfaz de usuario.

## <a name="advantages-of-asynchronous-monikers"></a>Ventajas de los Monikers asincrónicos

Puede utilizar los monikers asincrónicos en:

- Descargar archivos de código y sin bloqueos.

- Descargar las propiedades de controles ActiveX sin bloqueos.

- Recibir notificaciones de progreso de descarga.

- Realizar un seguimiento del progreso y la información de estado listo.

- Proporcionar información de estado al usuario sobre el progreso.

- Permitir al usuario cancelar una descarga en cualquier momento.

## <a name="mfc-classes-for-asynchronous-monikers"></a>Clases MFC para Monikers asincrónicos

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) se deriva de [CMonikerFile](../mfc/reference/cmonikerfile-class.md), que a su vez se deriva [COleStreamFile](../mfc/reference/colestreamfile-class.md). Un `COleStreamFile` objeto que representa una secuencia de datos; un `CMonikerFile` de objeto usa un `IMoniker` para obtener los datos y un `CAsyncMonikerFile` objeto ello de forma asincrónica.

Monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y los controles ActiveX para proporcionar una interfaz de usuario con capacidad de respuesta durante las transferencias de archivos. Un buen ejemplo de esto es el uso de [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para controles ActiveX.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Clases MFC para rutas de acceso de datos en los controles ActiveX

Las clases MFC `CDataPathProperty` y [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implementar propiedades de controles ActiveX que se pueden cargar de forma asincrónica. Propiedades asincrónicas se cargan después de un inicio sincrónico. Controles ActiveX asincrónicos invocan repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante el proceso de exchange propiedad largas.

La clase `CDataPathProperty` se deriva de la clase `CAsyncMonikerFile`. La clase `CCachedDataPathProperty` se deriva de la clase `CDataPathProperty`. Para implementar propiedades asincrónicas en los controles ActiveX, derive una clase de `CDataPathProperty` o `CCachedDataPathProperty`e invalidar [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) y otras notificaciones desea recibir.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Para descargar un archivo mediante monikers asincrónicos

1. Declarar una clase derivada de [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

1. Invalidar [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) para mostrar los datos.

1. Reemplazar otras funciones miembro, incluidos [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), y [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).

1. Declare una instancia de esta clase y utilizarla para abrir direcciones URL.

Para obtener información sobre la descarga de forma asincrónica en un control ActiveX, vea [controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md).

## <a name="see-also"></a>Vea también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

