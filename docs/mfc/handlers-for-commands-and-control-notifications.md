---
title: "Controladores de comandos y notificaciones de control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "comandos, controladores para"
  - "controles [MFC], notificaciones"
  - "funciones [C++], controlador"
  - "controladores"
  - "controladores, comando"
  - "controladores, notificación de control"
  - "notificaciones, controladores para controles"
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controladores de comandos y notificaciones de control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No hay controladores predeterminados para los comandos o mensajes de la CONTROL\- notificación.  Por consiguiente, la convención de nomenclatura se enlaza sólo controladores para estas categorías de mensajes.  Cuando asigna la notificación de comando o a un controlador, las ventanas Propiedades proponen un nombre basado en el código del identificador o la CONTROL\- notificación de comando.  Puede aceptar el nombre propuesto, cambiarlo, o reemplazarlo.  
  
 La convención sugiere que llama a los controladores de las categorías para el objeto de la interfaz de usuario que representan.  Así un controlador para el comando cortar en el menú Edición podría llamar  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/CPP/handlers-for-commands-and-control-notifications_1.h)]  
  
 Dado que implementan el comando cortar tan normalmente en aplicaciones, el marco predefine el identificador de comando para el comando cortar como **ID\_EDIT\_CUT**.  Para obtener una lista de todos los id. predefinidos de comando, vea el archivo AFXRES.H.  Para obtener más información, vea [Comandos estándar](../mfc/standard-commands.md).  
  
 Además, la convención sugiere un controlador para el mensaje de notificación de **BN\_CLICKED** de un botón “mi botón” podría llamar  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/CPP/handlers-for-commands-and-control-notifications_2.h)]  
  
 Podría asignar este comando un identificador de `IDC_MY_BUTTON` porque es equivalente a un objeto específico de la aplicación de la interfaz de usuario.  
  
 Las categorías de mensajes no toman ningún argumento y no devuelve ningún valor.  
  
## Vea también  
 [Declarar funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)