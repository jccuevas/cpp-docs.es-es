---
title: Agregar controles a una hoja de propiedades | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8437fcdaa04ce7dd2b0a214e4bd3a63ca421d014
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341096"
---
# <a name="adding-controls-to-a-property-sheet"></a>Agregar controles a una hoja de propiedades
De forma predeterminada, una hoja de propiedades asigna el área de la ventana para las páginas de propiedades, el índice de tabulación y los botones Aceptar, Cancelar y aplicar. (Una hoja de propiedades no modal no tiene Aceptar, Cancelar y aplicar botones.) Puede agregar otros controles a la hoja de propiedades. Por ejemplo, puede agregar una ventana de vista previa a la derecha del área de página de propiedades para mostrar al usuario cuál sería la configuración actual si se aplica a un objeto externo.  
  
 Puede agregar controles al cuadro de diálogo de hoja de propiedades en el `OnCreate` controlador. Alojar controles adicionales normalmente necesita aumentar el tamaño del cuadro de diálogo de hoja de propiedades. Después de llamar a la clase base **CPropertySheet:: OnCreate**, llame a [GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect) para obtener el ancho y alto de la ventana de la hoja de propiedades asignada actualmente, expanda el rectángulo dimensiones y llamada [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) para cambiar el tamaño de la ventana de la hoja de propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)   
 [CPropertyPage (clase)](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet (clase)](../mfc/reference/cpropertysheet-class.md)
