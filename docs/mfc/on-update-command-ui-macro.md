---
title: ON_UPDATE_COMMAND_UI (Macro)
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 2a3f097a44e96fc470719ce636cc1b73e676fb38
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095847"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI (Macro)

Para conectar un objeto de interfaz de usuario a un controlador de actualización de comandos en un objeto de destino de comando, Abra **vista de clases**, haga clic con el botón derecho en la clase a la que se agregará el controlador y elija **Asistente para clases**. Busque el identificador del objeto de la interfaz de usuario en la lista de la izquierda, elija **UPDATE_COMMAND_UI** en el panel derecho y haga clic en **Agregar controlador**. Esto crea una función de controlador en la clase y agrega la entrada adecuada en el mapa de mensajes. Vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información. Puede especificar mensajes adicionales para controlar en el panel **mensajes** .

Por ejemplo, para actualizar un comando CLEAR ALL en el menú Editar del programa, use el **Asistente para clases** para agregar una entrada de mapa de mensajes en la clase seleccionada, una declaración de función para un controlador de `OnUpdateEditClearAll` actualización de comandos llamado en la declaración de clase y un elemento vacío plantilla de función en el archivo de implementación de la clase. El prototipo de función tiene el siguiente aspecto:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Al igual que todos los controladores, la declaración de función muestra la palabra clave **afx_msg** . Al igual que todos los controladores de actualización, toma un argumento, un puntero `CCmdUI` a un objeto.

## <a name="see-also"></a>Vea también

[Cómo: actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)
