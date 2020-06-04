---
title: Mapas de mensajes (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356576"
---
# <a name="message-maps-mfc"></a>Mapas de mensajes (MFC)

Esta sección de la referencia enumera todas las macros de [asignación](../../mfc/reference/message-map-macros-mfc.md) de mensajes y todas las entradas de mapa de mensajes [CWnd](../../mfc/reference/cwnd-class.md) junto con los prototipos de función miembro correspondientes:

|Category|Descripción|
|--------------|-----------------|
|ON\_COMMAND Controlador de mensajes|Controla los `WM_COMMAND` mensajes generados por las selecciones de menú de usuario o las teclas de acceso al menú.|
|[Controladores de mensajes de ventanas secundarias](../../mfc/reference/child-window-notification-message-handlers.md)|Controlan los mensajes de notificación de las ventanas secundarias.|
|[controladores de mensajes WM_](../../mfc/reference/handlers-for-wm-messages.md)|Controlar `WM_` mensajes, `WM_PAINT`como .|
|[Controladores de mensajes definidos por el usuario](../../mfc/reference/user-defined-handlers.md)|Controlan los mensajes definidos por el usuario.|

(Para obtener una explicación de la terminología y las convenciones utilizadas en esta referencia, consulte [Cómo utilizar la referencia cruzada](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)del mapa de mensajes .)

Puesto que Windows es un sistema operativo orientado a mensajes, una gran parte de la programación para el entorno Windows implica el control de mensajes. Cada vez que tiene lugar un evento como una pulsación de tecla o un clic del mouse, se envía un mensaje a la aplicación, que debe controlar el evento.

La biblioteca MFC (Microsoft Foundation Class) proporciona un modelo de programación optimizado para la programación basada en mensajes. En este modelo, los "mapas de mensajes" se utilizan para designar qué funciones controlarán los distintos mensajes para una clase determinada. Los mapas de mensajes contienen una o varias macros que especifican qué mensajes se controlan mediante qué funciones. Por ejemplo, un mapa de mensajes que contiene una macro `ON_COMMAND` podría tener la siguiente apariencia:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

La macro `ON_COMMAND` se utiliza para controlar los mensajes de comando generados por los menús, los botones y las teclas de aceleración. [Las macros](../../mfc/reference/message-map-macros-mfc.md) están disponibles para asignar lo siguiente:

## <a name="windows-messages"></a>Mensajes de Windows

- Notificaciones del control

- Mensajes definidos por el usuario

## <a name="command-messages"></a>Mensajes de comando

- Mensajes definidos por el usuario registrados

- Mensajes de actualización de la interfaz de usuario

## <a name="ranges-of-messages"></a>Intervalos de mensajes

- Comandos:

- Mensajes del controlador de actualización

- Notificaciones del control

Aunque las macros de mapa de mensajes son importantes, en general no es necesario utilizarlas directamente. Esto se debe a que el [Asistente para clases](mfc-class-wizard.md) crea automáticamente entradas de mapa de mensajes en los archivos de origen cuando se utiliza para asociar funciones de control de mensajes con mensajes. Cada vez que desee editar o agregar una entrada de mapa de mensajes, puede utilizar el Asistente para clases.

> [!NOTE]
> El Asistente para clases no admite intervalos de mapa de mensajes. Debe escribir estas entradas de mapa de mensajes manualmente.

Sin embargo, los mapas de mensajes son una parte importante de la biblioteca MFC (Microsoft Foundation Class). Debe entender lo que hacen y consultar la documentación que se proporciona sobre ellos.

## <a name="see-also"></a>Consulte también

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
