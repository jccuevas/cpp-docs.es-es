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
ms.openlocfilehash: cc89cbfde0a1eba5dc736b40c178d4a4fde37a4d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625765"
---
# <a name="handlers-for-commands-and-control-notifications"></a>Controladores de comandos y notificaciones de control

No hay controladores predeterminados para los comandos o los mensajes de notificación de control. Por lo tanto, solo se enlaza por Convención en el nombre de los controladores de estas categorías de mensajes. Cuando se asigna la notificación de comando o control a un controlador, el [Asistente para clases](reference/mfc-class-wizard.md) propone un nombre basado en el identificador de comando o el código de notificación de control. Puede aceptar el nombre propuesto, cambiarlo o reemplazarlo.

La Convención sugiere que se asignen nombres a los controladores de ambas categorías para el objeto de interfaz de usuario que representan. Por lo tanto, un controlador para el comando cortar en el menú Edición podría denominarse

[!code-cpp[NVC_MFCMessageHandling#4](codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

Dado que el comando CUT se implementa normalmente en aplicaciones, el marco de trabajo predefine el identificador de comando para el comando CUT como **ID_EDIT_CUT**. Para obtener una lista de todos los identificadores de comandos predefinidos, vea el archivo AFXRES. C. Para obtener más información, vea [comandos estándar](standard-commands.md).

Además, la Convención sugiere un controlador para que el mensaje de notificación de **BN_CLICKED** desde un botón "mi botón" se denomine

[!code-cpp[NVC_MFCMessageHandling#5](codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

Podría asignar este comando a un identificador de **IDC_MY_BUTTON** porque es equivalente a un objeto de interfaz de usuario específico de la aplicación.

Ambas categorías de mensajes no toman ningún argumento y no devuelven ningún valor.

## <a name="see-also"></a>Consulte también

[Declarar funciones del controlador de mensajes](declaring-message-handler-functions.md)
