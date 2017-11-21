---
title: "Selección de elementos de Control de árbol | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fac551ed757cf0510f0a8b61522bc969c6b6be6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="tree-control-item-selection"></a>Selección de elementos de control de árbol
Cuando se cambia la selección de un elemento a otro, un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía [TVN_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) y [TVN_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) mensajes de notificación. Ambas notificaciones incluyen un valor que especifica si el cambio es el resultado de un clic del mouse o una pulsación de tecla. Las notificaciones también incluyen información sobre el elemento que está adquiriendo cada vez la selección y el elemento que está perdiendo la selección. Puede utilizar esta información para establecer atributos de elemento que dependen del estado de selección del elemento. Devolver **TRUE** en respuesta a **TVN_SELCHANGING** impide realizar la selección del cambio; devolver **FALSE** permite el cambio.  
  
 Una aplicación puede cambiar la selección mediante una llamada a la [función miembro SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

