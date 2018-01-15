---
title: "Cómo: actualizar los objetos de interfaz de usuario | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 91e6d13e840c29d3ea9600183fafd9260966a2f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-update-user-interface-objects"></a>Cómo: Actualizar objetos de la interfaz de usuario
Normalmente, los elementos de menú y botones de barra de herramientas tienen más de un estado. Por ejemplo, un elemento de menú está deshabilitado (atenuado) si no está disponible en este contexto. Elementos de menú también puede activar o desactivar. Un botón de barra de herramientas también puede deshabilitarse si no está disponible o se pueda proteger.  
  
 Que actualiza el estado de estos elementos como programa cambian las condiciones lógicamente, si un elemento de menú genera un comando que se controla mediante, por ejemplo, un documento, tiene sentido que el documento actualice el elemento de menú. El documento contiene probablemente la información en el que se basa la actualización.  
  
 Si un comando tiene varios objetos de interfaz de usuario (quizás un elemento de menú y un botón de barra de herramientas), ambos se enrutan a la misma función de controlador. Esto encapsula el código de actualización de la interfaz de usuario para todos los objetos de interfaz de usuario equivalentes en un único lugar.  
  
 El marco de trabajo proporciona una interfaz adecuada para actualizar automáticamente los objetos de interfaz de usuario. Puede elegir hacer la actualización de otra forma, pero la interfaz proporcionada es eficaz y fácil de usar.  
  
 Los temas siguientes explican el uso de controladores de actualización:  
  
-   [Cuando se llama a los controladores de actualización](../mfc/when-update-handlers-are-called.md)  
  
-   [La macro ON_UPDATE_COMMAND_UI](../mfc/on-update-command-ui-macro.md)  
  
-   [CCmdUI (clase)](../mfc/the-ccmdui-class.md)  
  
## <a name="see-also"></a>Vea también  
 [Menús](../mfc/menus-mfc.md)

