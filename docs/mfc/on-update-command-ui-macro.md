---
title: ON_UPDATE_COMMAND_UI (Macro)
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 986bc4f12223048a20f88da5d164b24dc1c08ace
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261185"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI (Macro)

Use la **propiedades** ventana para conectarse a un objeto de interfaz de usuario a un controlador de actualización de comandos en un objeto de destino del comando. Automáticamente se conectará el Id. del objeto de interfaz de usuario a la macro ON_UPDATE_COMMAND_UI y crear un controlador en el objeto que va a controlar la actualización. Consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información.

Por ejemplo, para actualizar un comando Borrar todo en el menú de edición del programa, use la **propiedades** ventana para agregar una entrada de mapa de mensajes en la clase seleccionada, una declaración de función para un controlador de actualización de comandos denominada `OnUpdateEditClearAll` en la clase declaración y una plantilla de función vacíos en el archivo de implementación de la clase. El prototipo de función tiene este aspecto:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Al igual que todos los controladores, se muestra en la función la **afx_msg** palabra clave. Al igual que todos los controladores de actualización, toma un argumento, un puntero a un `CCmdUI` objeto.

## <a name="see-also"></a>Vea también

[Cómo: Actualizar los objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)
