---
title: Agregar pestañas a un Control de ficha | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb8caad0b7d1f632a2d97e4ea6bda7c93a2b4d74
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218302"
---
# <a name="adding-tabs-to-a-tab-control"></a>Agregar pestañas a un control de pestaña
Después de crear el control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), agregar tantas pestañas como sea necesario.  
  
### <a name="to-add-a-tab-item"></a>Para agregar un elemento de pestaña  
  
1.  Preparar una [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura.  
  
2.  Llame a [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), pasando la estructura.  
  
3.  Repita los pasos 1 y 2 para los elementos de una ficha adicional.  
  
 Para obtener más información, consulte [creación de un Control de ficha](/windows/desktop/Controls/tab-controls) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)

