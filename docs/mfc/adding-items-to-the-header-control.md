---
title: Agregar elementos al Control de encabezado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69d64265a94df2770e3a234ab992130b4809f9e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342740"
---
# <a name="adding-items-to-the-header-control"></a>Agregar elementos al control de encabezado
Después de crear el control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) en su ventana primaria, agregue tantos "elementos de encabezado" según sea necesario: normalmente uno por cada columna.  
  
### <a name="to-add-a-header-item"></a>Para agregar un elemento de encabezado  
  
1.  Preparar una [estructura HD_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) estructura.  
  
2.  Llame a [:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), pasando la estructura.  
  
3.  Repita los pasos 1 y 2 para elementos adicionales.  
  
 Para obtener más información, consulte [agregar un elemento a un Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775238) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

