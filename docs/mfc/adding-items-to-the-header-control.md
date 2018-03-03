---
title: Agregar elementos al Control de encabezado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4de62d534da103f17df113b04b88021561739cfc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

