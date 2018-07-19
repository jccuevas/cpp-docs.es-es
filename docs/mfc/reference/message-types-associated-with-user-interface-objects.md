---
title: Tipos asociados a objetos de interfaz de usuario de mensajes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7ecc948910dd618f343134b0e9e3133539d9e1f
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335485"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Tipos de mensajes asociados a objetos de la interfaz de usuario
En la tabla siguiente se muestra los tipos de objetos con las que trabaja y los tipos de mensajes asociados con ellos.  
  
### <a name="user-interface-objects-and-associated-messages"></a>Objetos de la interfaz de usuario y los mensajes asociados  
  
|Id. de objeto|Mensajes|  
|---------------|--------------|  
|Nombre de clase, que representa la ventana contenedora|Mensajes de Windows apropiados para una [CWnd](../../mfc/reference/cwnd-class.md)-clase derivada: un cuadro de diálogo, ventanas, ventana secundaria, ventana secundaria MDI o marco de nivel superior.|  
|Identificador de menú o tecla aceleradora|-Mensaje de comando (ejecuta la función del programa).<br />-Mensaje UPDATE_COMMAND_UI (actualiza dinámicamente el elemento de menú).|  
|Identificador de control|Controlar mensajes de notificación para el tipo de control seleccionado.|  
  
## <a name="see-also"></a>Vea también  
 [Asignar mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Adición de un controlador de mensajes MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
