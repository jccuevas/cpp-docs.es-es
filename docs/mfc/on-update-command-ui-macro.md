---
title: ON_UPDATE_COMMAND_UI (macro) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ON_UPDATE_COMMAND_UI
dev_langs: C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3de873cf70bafa77d7c8f4b05c70ce211b2c2258
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI (Macro)
Use la **propiedades** ventana para conectar un objeto de interfaz de usuario a un controlador de actualización de comandos en un objeto de destino del comando. Conectará automáticamente el identificador del objeto de interfaz de usuario para el `ON_UPDATE_COMMAND_UI` macro y crear un controlador en el objeto que controlará la actualización. Vea [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información.  
  
 Por ejemplo, para actualizar un comando Borrar todo en el menú de edición del programa, use la **propiedades** ventana para agregar una entrada de mapa de mensajes en la clase seleccionada, una declaración de función para un controlador de actualización de comandos denominada `OnUpdateEditClearAll` en la clase declaración y una plantilla de función vacía en el archivo de implementación de la clase. El prototipo de función tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 Al igual que todos los controladores, la función se muestra la **afx_msg** palabra clave. Al igual que todos los controladores de actualización, toma un argumento, un puntero a un `CCmdUI` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Procedimiento para actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)

