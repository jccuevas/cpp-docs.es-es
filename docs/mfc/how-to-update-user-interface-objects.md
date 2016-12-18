---
title: "C&#243;mo: Actualizar objetos de la interfaz de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "comandos, actualizar UI"
  - "deshabilitar menús"
  - "deshabilitar elementos UI"
  - "habilitar menús"
  - "habilitar elementos UI"
  - "menús, actualizar cuando el contexto cambia"
  - "controladores de actualización"
  - "actualizar objetos de la interfaz de usuario"
  - "objetos de interfaz de usuario"
  - "objetos de interfaz de usuario, actualizar"
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Actualizar objetos de la interfaz de usuario
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Normalmente, los elementos de menú y botones de la barra de herramientas tienen más de un estado.  Por ejemplo, se atenúa un elemento de menú \(atenuada\) si no está disponible en el contexto actual.  Los elementos de menú también pueden comprobarse o ser desactivados.  Un botón de la barra de herramientas también puede estar deshabilitado si no está disponible, o puede activarse.  
  
 ¿Quién actualiza el estado de estos elementos como cambio de condiciones de programa?  Lógicamente, si un elemento de menú genera un comando que es administrado por, por ejemplo, un documento, tiene sentido de tener el documento actualiza el elemento de menú.  El documento probablemente contiene información en la que se basa la actualización.  
  
 Si un comando tiene varios objetos de la interfaz de usuario \(quizás un elemento de menú y un botón de la barra de herramientas\), ambos se enrutan a la misma función de controlador.  Esto encapsula el código de actualización de la interfaz de usuario para todos los objetos equivalentes de la interfaz de usuario en un solo lugar.  
  
 El marco de trabajo proporciona una interfaz conveniente para actualizar automáticamente los objetos de la interfaz de usuario.  Puede elegir actualizar de alguna otra manera, pero la interfaz proporcionada es eficaz y fácil de usar.  
  
 Los temas siguientes explican el uso de controladores actualizados:  
  
-   [Cuando se llama a los controladores de actualización](../mfc/when-update-handlers-are-called.md)  
  
-   [La macro ON\_UPDATE\_COMMAND\_UI](../mfc/on-update-command-ui-macro.md)  
  
-   [La clase de CCmdUI](../mfc/the-ccmdui-class.md)  
  
## Vea también  
 [Menus](../mfc/menus-mfc.md)