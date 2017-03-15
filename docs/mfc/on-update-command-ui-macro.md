---
title: "ON_UPDATE_COMMAND_UI (Macro) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_UPDATE_COMMAND_UI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros de controlador para comandos"
  - "ON_UPDATE_COMMAND_UI (macro)"
  - "controladores de actualización"
  - "actualizar objetos de la interfaz de usuario"
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ON_UPDATE_COMMAND_UI (Macro)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice la ventana de **Propiedades** para conectar un objeto de la interfaz de usuario a un controlador de la comando\- actualización en un objeto de comando\- destino.  Automáticamente conectar el identificador de objeto de la interfaz de usuario a la macro de `ON_UPDATE_COMMAND_UI` y creará un controlador en el objeto que administrará la actualización.  Vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para obtener más información.  
  
 Por ejemplo, para actualizar un comando claro Todo en el menú Edición del programa, utilice la ventana de **Propiedades** para agregar una entrada de mensaje\- mapa en la clase especificada, una declaración de función para un controlador de la comando\- actualización denominado `OnUpdateEditClearAll` en la declaración de clase, y una plantilla vacía de la función en el archivo de implementación de la clase.  El prototipo de función tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/CPP/on-update-command-ui-macro_1.h)]  
  
 Como todos los controladores, la función muestra la palabra clave de **afx\_msg** .  Como todos actualice controladores, que toma un argumento, un puntero a un objeto de `CCmdUI` .  
  
## Vea también  
 [Cómo: Actualizar objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)