---
title: Agregar pestañas a un Control de pestaña | Documentos de Microsoft
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
ms.openlocfilehash: 86032bd3d1ce10221cb5d8094e4ba6de866e1eea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342858"
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

