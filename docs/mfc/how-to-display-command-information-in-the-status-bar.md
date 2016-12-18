---
title: "C&#243;mo: Mostrar informaci&#243;n de comandos en la barra de estado | Microsoft Docs"
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
  - "mostrar estado de comandos"
  - "mensajes [C++]"
  - "barras de estado, mostrar información de comandos"
  - "barras de estado, área del mensaje"
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Mostrar informaci&#243;n de comandos en la barra de estado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al ejecutar el Asistente para aplicaciones para crear la estructura de la aplicación, puede admitir una barra de herramientas y una barra de estado.  Simplemente una opción en el Asistente para aplicaciones MFC admite ambos.  Cuando una barra de estado está presente, la aplicación proporciona automáticamente información útil cuando el usuario mueve el puntero sobre elementos de menús.  La aplicación muestra automáticamente una cadena de solicitud en la barra de estado cuando se resalta el elemento de menú.  Por ejemplo, cuando el usuario mueve el puntero sobre el comando de **Cortado** en el menú de **edición** , la barra de estado puede mostrar los “cortes la selección y la coloca en el portapapeles” en el área de mensajes de la barra de estado.  El marcador ayuda a entender el propósito del elemento de menú.  Esto también funciona cuando el usuario hace clic en un botón de la barra de herramientas.  
  
 Puede agregar a esta ayuda de barra de estado definiendo las cadenas de mensajes para los elementos de menú que se agrega al programa.  Para ello, especifique las cadenas de mensajes cuando se modifican las propiedades del elemento en el editor de menús.  Las cadenas que defina se almacenan en el archivo de recursos de la aplicación; tienen los mismos id. que los comandos se explican.  
  
 De forma predeterminada, el Asistente para aplicaciones agrega `AFX_IDS_IDLEMESSAGE`, el identificador de un mensaje estándar de " listo ", que se muestra cuando el programa está esperando mensajes nuevos.  Si especifica la opción de ayuda contextual en el Asistente para aplicaciones, el mensaje se cambia a “Ayuda For, presione F1”.  
  
## Vea también  
 [Controlar y asignar mensajes](../mfc/message-handling-and-mapping.md)