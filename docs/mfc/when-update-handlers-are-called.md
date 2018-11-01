---
title: Cuándo se llama a los controladores actualizados
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
ms.openlocfilehash: 036476ecc7a0528692e6fd3e3d69a2efeef6fd4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454852"
---
# <a name="when-update-handlers-are-called"></a>Cuándo se llama a los controladores actualizados

Supongamos que el usuario hace clic en el mouse en el menú archivo, que genera un mensaje WM_INITMENUPOPUP. Mecanismo de actualización de .NET framework colectivamente actualiza todos los elementos en el menú archivo antes de que el menú se despliega para que el usuario pueda verla.

Para ello, el marco de trabajo enruta comandos de actualización para todos los elementos de menú en el menú emergente junto con el enrutamiento de comandos estándar. Destinos de comando en la ruta tienen la oportunidad de actualizar los elementos del menú haciendo coincidir el comando de actualización con una entrada de mapa de mensajes adecuado (del formulario `ON_UPDATE_COMMAND_UI`) y llamada a una función "controlador de actualización". Por lo tanto, para un menú con seis elementos de menú, seis comandos de actualización se envíen. Si existe un controlador de actualización para el identificador de comando del elemento de menú, se llama para realizar la actualización. De lo contrario, el marco de trabajo comprueba la existencia de un controlador para ese identificador de comando y habilita o deshabilita el elemento de menú según corresponda.

Si el marco de trabajo no se encuentra un `ON_UPDATE_COMMAND_UI` entrada durante el enrutamiento de comandos, habilita automáticamente el objeto de interfaz de usuario si no hay un `ON_COMMAND` entrada en algún lugar con el mismo identificador de comando. En caso contrario, deshabilita el objeto de interfaz de usuario. Por lo tanto, para asegurarse de que un objeto de interfaz de usuario está habilitado, proporcione un controlador para el comando que genera el objeto o proporcionar un controlador de actualización para él. Consulte la figura en el tema [objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md).

Es posible deshabilitar la deshabilitación predeterminado de objetos de interfaz de usuario. Para obtener más información, consulte el [miembro m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) miembro de clase `CFrameWnd` en el *referencia de MFC*.

Inicialización menú es automática en el marco de trabajo, que se producen cuando la aplicación recibe un mensaje WM_INITMENUPOPUP. Durante el bucle de inactividad, el marco de trabajo busca el enrutamiento de comandos para los controladores del botón de actualización de la misma manera que lo hace para los menús.

## <a name="see-also"></a>Vea también

[Procedimiento para actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)

