---
title: Monikers asincrónicos en Internet
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: 74add1ad894f883c67eefab888898c0abf518b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625034"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Monikers asincrónicos en Internet

Internet requiere nuevos enfoques para el diseño de aplicaciones debido a su acceso lento a la red. Las aplicaciones deben realizar el acceso a la red de forma asincrónica para evitar la detención de la interfaz de usuario. La clase MFC [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) proporciona compatibilidad asincrónica para descargar archivos.

Con monikers asincrónicos, puede ampliar la aplicación COM para que descargue de forma asincrónica a través de Internet y para proporcionar una representación progresiva de objetos grandes, como mapas de bits y objetos VRML. Los monikers asincrónicos permiten descargar una propiedad de control ActiveX o un archivo en Internet sin bloquear la respuesta de la interfaz de usuario.

## <a name="advantages-of-asynchronous-monikers"></a>Ventajas de los monikers asincrónicos

Puede usar monikers asincrónicos para:

- Descargar código y archivos sin bloqueos.

- Descargar propiedades en controles ActiveX sin bloqueos.

- Recibir notificaciones de progreso de la descarga.

- Realice un seguimiento de la información de estado y preparación.

- Proporcionar información de estado al usuario sobre el progreso.

- Permite al usuario cancelar una descarga en cualquier momento.

## <a name="mfc-classes-for-asynchronous-monikers"></a>Clases MFC para monikers asincrónicos

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md) se deriva de [CMonikerFile](reference/cmonikerfile-class.md), que a su vez se deriva de [COleStreamFile](reference/colestreamfile-class.md). Un `COleStreamFile` objeto representa una secuencia de datos; un `CMonikerFile` objeto utiliza `IMoniker` para obtener los datos y un `CAsyncMonikerFile` objeto lo hace de forma asincrónica.

Los monikers asincrónicos se utilizan principalmente en aplicaciones habilitadas para Internet y controles ActiveX para proporcionar una interfaz de usuario con capacidad de respuesta durante las transferencias de archivos. Un ejemplo primo es el uso de [CDataPathProperty](reference/cdatapathproperty-class.md) para proporcionar propiedades asincrónicas para los controles ActiveX.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Clases MFC para rutas de acceso de datos en controles ActiveX

Las clases `CDataPathProperty` y [CCACHEDDATAPATHPROPERTY](reference/ccacheddatapathproperty-class.md) de MFC implementan propiedades de controles ActiveX que se pueden cargar de forma asincrónica. Las propiedades asincrónicas se cargan después del inicio sincrónico. Los controles ActiveX asincrónicos invocan repetidamente una devolución de llamada para indicar la disponibilidad de nuevos datos durante un proceso de intercambio de propiedades prolongado.

La clase `CDataPathProperty` se deriva de la clase `CAsyncMonikerFile`. La clase `CCachedDataPathProperty` se deriva de la clase `CDataPathProperty`. Para implementar propiedades asincrónicas en los controles ActiveX, derive una clase de `CDataPathProperty` o `CCachedDataPathProperty` , e invalide [ondataavailable](reference/casyncmonikerfile-class.md#ondataavailable) y otras notificaciones que desee recibir.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Para descargar un archivo mediante monikers asincrónicos

1. Declare una clase derivada de [CAsyncMonikerFile](reference/casyncmonikerfile-class.md).

1. Reemplace [ondataavailable](reference/casyncmonikerfile-class.md#ondataavailable) para mostrar los datos.

1. Invalide otras funciones miembro, como [OnProgress](reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](reference/casyncmonikerfile-class.md#onstartbinding)y [OnStopBinding](reference/casyncmonikerfile-class.md#onstopbinding).

1. Declare una instancia de esta clase y Úsela para abrir las direcciones URL.

Para obtener información sobre cómo descargar de forma asincrónica en un control ActiveX, vea [controles ActiveX en Internet](activex-controls-on-the-internet.md).

## <a name="see-also"></a>Consulte también

[Tareas de programación para Internet de MFC](mfc-internet-programming-tasks.md)<br/>
[Fundamentos de la programación para Internet de MFC](mfc-internet-programming-basics.md)
