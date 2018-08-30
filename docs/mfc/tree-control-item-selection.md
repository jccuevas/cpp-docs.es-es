---
title: Selección de elementos de Control de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd6632a44dd4806b8f13683b50cad76b5eebe27a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212586"
---
# <a name="tree-control-item-selection"></a>Selección de elementos de control de árbol
Cuando se cambia la selección de un elemento a otro, un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) y [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) mensajes de notificación. Ambas notificaciones incluyen un valor que especifica si el cambio es el resultado de un clic del mouse o una pulsación de tecla. Las notificaciones también incluyen información sobre el elemento que está ganando la selección y el elemento que está perdiendo la selección. Puede usar esta información para establecer los atributos del elemento que dependen del estado de selección del elemento. Devolver **TRUE** en respuesta a `TVN_SELCHANGING` impide que la selección del cambio; devolver **FALSE** permite el cambio.  
  
 Una aplicación puede cambiar la selección mediante una llamada a la [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

