---
title: Controladores de comandos y notificaciones de control
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 28bed2937409cd1df5ee8d295e466609232e0e91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622058"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Controladores de comandos y notificaciones de control

No hay ningún controlador predeterminado para los comandos o los mensajes de notificación de control. Por lo tanto, se enlazan mediante la convención de nomenclatura de los controladores para estas categorías de mensajes. Al asignar la notificación de comando o un control a un controlador, la ventana Propiedades propone un nombre basado en el código de Id. o notificación de control de comandos. Puede aceptar el nombre propuesto, cambiarlo o reemplazarlo.

Convención sugiere el nombre de los controladores en ambas categorías para el objeto de interfaz de usuario que representan. Por lo tanto podría denominar un controlador para el comando Cortar en el menú Edición

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Dado que el comando Cortar por lo que normalmente se implementa en las aplicaciones, el marco de trabajo predefine el identificador de comando para el comando Cortar como **ID_EDIT_CUT**. Para obtener una lista de todos los identificadores de comando predefinidos, vea el archivo AFXRES. H. Para obtener más información, consulte [comandos estándar](../mfc/standard-commands.md).

Además, la convención sugiere un controlador para el **BN_CLICKED** podría denominar el mensaje de notificación de un botón denominado "Mi botón"

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Puede asignar un Id. de este comando **IDC_MY_BUTTON** porque es equivalente a un objeto de interfaz de usuario específica de la aplicación.

Las dos categorías de mensajes no toman ningún argumento y no devuelven ningún valor.

## <a name="see-also"></a>Vea también

[Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
