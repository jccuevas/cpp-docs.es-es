---
title: "Agregar pestañas a un Control de pestaña | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46012a265c1ecefa7af63f829be22e6132e036cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-tabs-to-a-tab-control"></a>Agregar pestañas a un control de pestaña
Después de crear el control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), agregar tantas pestañas según sea necesario.  
  
### <a name="to-add-a-tab-item"></a>Para agregar un elemento de pestaña  
  
1.  Preparar una [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) estructura.  
  
2.  Llame a [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), pasando la estructura.  
  
3.  Repita los pasos 1 y 2 para elementos de ficha adicionales.  
  
 Para obtener más información, consulte [crear un Control de ficha](http://msdn.microsoft.com/library/windows/desktop/bb760550) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)

