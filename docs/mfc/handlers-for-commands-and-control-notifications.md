---
title: Controladores de comandos y notificaciones de Control | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e6492c6ecc4c21c5c978ad031fed7182f2acee4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="handlers-for-commands-and-control-notifications"></a>Controladores de comandos y notificaciones de control
No hay ningún controlador predeterminado para comandos o mensajes de notificación de control. Por lo tanto, se enlazan solo por la convención de nomenclatura de los controladores para estas categorías de mensajes. Al asignar la notificación de comando o un control a un controlador, la ventana Propiedades propone un nombre basado en el código de Id. o notificación de control de comandos. Puede aceptar el nombre propuesto, cambiarlo o reemplazarlo.  
  
 Convención sugiere que nombrar los controladores de ambas categorías para el objeto de interfaz de usuario que representan. Por lo tanto podría llamarse un controlador para el comando Cortar en el menú Edición  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]  
  
 Dado que el comando Cortar por lo que normalmente se implementa en las aplicaciones, el marco de trabajo predefine el identificador de comando para el comando Cortar como **ID_EDIT_CUT**. Para obtener una lista de todos los identificadores de comando predefinidos, vea el archivo AFXRES. H. Para obtener más información, consulte [comandos estándar](../mfc/standard-commands.md).  
  
 Además, la convención sugiere un controlador para el **BN_CLICKED** podría llamarse mensaje de notificación de un botón denominado "Mi botón"  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]  
  
 Puede asignar un Id. de este comando `IDC_MY_BUTTON` porque es equivalente a un objeto de interfaz de usuario específica de la aplicación.  
  
 Las dos categorías de mensajes no toman ningún argumento y no devuelven ningún valor.  
  
## <a name="see-also"></a>Vea también  
 [Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
