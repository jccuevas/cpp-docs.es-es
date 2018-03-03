---
title: Usar CHotKeyCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CHotKeyCtrl
dev_langs:
- C++
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36d577369dea4f5fe2fffa9801bbd8ae8501f71a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-chotkeyctrl"></a>Usar CHotKeyCtrl
Un control hot key, representado por la clase [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), es una ventana que muestra una representación de texto de la combinación de teclas que el usuario escribe en él, por ejemplo, CTRL + MAYÚS + Q. También mantiene una representación interna de esta clave en el formato de un código de tecla virtual y un conjunto de marcas que representan el estado de desplazamiento. El control de tecla de acceso rápido realmente no se establece la tecla de acceso rápido: hacer que depende de su programa. (Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h.)  
  
 Usar un control de tecla de acceso rápido para obtener la entrada de un usuario para qué tecla de acceso rápido asociar a una ventana o un subproceso. Controles de tecla de acceso rápidos a menudo se usan en los cuadros de diálogo, como podría mostrar cuando se solicita al usuario que asigne una tecla de acceso rápido. Es responsabilidad de su programa para recuperar los valores que describen la tecla de acceso rápido desde el control de tecla de acceso rápido y llamar a las funciones adecuadas para asociar la tecla de acceso rápido a una ventana o un subproceso.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Uso de un control de tecla de acceso directo](../mfc/using-a-hot-key-control.md)  
  
-   [Establecimiento de una tecla de acceso directo](../mfc/setting-a-hot-key.md)  
  
-   [Teclas de acceso directo globales](../mfc/global-hot-keys.md)  
  
-   [Teclas de acceso directo específicas del subproceso](../mfc/thread-specific-hot-keys.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles](../mfc/controls-mfc.md)

