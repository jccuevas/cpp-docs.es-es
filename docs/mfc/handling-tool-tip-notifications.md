---
title: "Control de las notificaciones de información sobre herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- CToolBarCtrl class [MFC], handling notifications
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b7668420b849dc08215a4fc309edf86e9171462
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="handling-tool-tip-notifications"></a>Controlar las notificaciones de información sobre herramientas
Cuando se especifica la `TBSTYLE_TOOLTIPS` estilo, la barra de herramientas crea y administra un control de información sobre herramientas. Una información sobre herramientas es una pequeña ventana emergente que contiene una línea de texto que describe un botón de barra de herramientas. La información sobre herramientas está oculta, que aparecen solo cuando el usuario coloca el cursor sobre un botón de barra de herramientas y deja ahí durante, aproximadamente, medio segundo. La información sobre herramientas aparece cerca del cursor.  
  
 Antes de que se muestre la información sobre herramientas, el **TTN_NEEDTEXT** mensaje de notificación se envía a la ventana propietaria de la barra de herramientas para recuperar el texto descriptivo para el botón. Si la ventana propietaria de la barra de herramientas es un `CFrameWnd` ventana, herramienta de sugerencias se muestran sin ningún esfuerzo adicional, porque `CFrameWnd` tiene un controlador predeterminado para la **TTN_NEEDTEXT** notificación. Si la ventana propietaria de la barra de herramientas no se deriva de `CFrameWnd`, por ejemplo, una vista de formulario o de cuadro de diálogo, debe agregar una entrada al mapa de mensajes de la ventana propietaria y proporcionar un controlador de notificación en el mapa de mensajes. La entrada al mapa de mensajes de la ventana propietaria es como sigue:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-tool-tip-notifications_1.cpp)]  
  
## <a name="remarks"></a>Comentarios  
 `memberFxn`  
 La función miembro se llama cuando es necesario el texto para que este botón.  
  
 Tenga en cuenta que el identificador de una información sobre herramientas siempre es 0.  
  
 Además el **TTN_NEEDTEXT** notificación, un control de información sobre herramientas puede enviar las siguientes notificaciones a un control de barra de herramientas:  
  
|notificación|Significado|  
|------------------|-------------|  
|**TTN_NEEDTEXTA**|Control de información sobre herramientas requiere texto ASCII (sólo en Windows 95)|  
|**TTN_NEEDTEXTW**|Control de información sobre herramientas requiere texto UNICODE (sólo Windows NT)|  
|**TBN_HOTITEMCHANGE**|Indica que el elemento activo (resaltado) ha cambiado.|  
|**NM_RCLICK**|Indica que el usuario ha hecho un botón.|  
|**TBN_DRAGOUT**|Indica que el usuario tiene clic con el botón y arrastrar el puntero fuera del botón. Permite que una aplicación para la implementación de arrastrar y colocar en un botón de barra de herramientas. Cuando se recibe esta notificación, la aplicación comenzar la operación de arrastrar y colocar la operación.|  
|**TBN_DROPDOWN**|Indica que el usuario hace clic en un botón que usa el **TBSTYLE_DROPDOWN** estilo.|  
|**TBN_GETOBJECT**|Indica que el usuario mueve el puntero sobre un botón que usa el **TBSTYLE_DROPPABLE** estilo.|  
  
 Para una función de controlador de ejemplo y obtener más información acerca de cómo habilitar la información sobre herramientas, vea [información sobre herramientas](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

