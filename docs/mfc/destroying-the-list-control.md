---
title: Destruir el Control de lista | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edb26671ba775cfa7daf98d39c7eccc9fd4111bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343287"
---
# <a name="destroying-the-list-control"></a>Destruir el control de lista
Si incrusta el [CListCtrl](../mfc/reference/clistctrl-class.md) objeto como un miembro de datos de una clase de vista o cuadro de diálogo, se destruye cuando se destruye su propietario. Si utiliza un [CListView](../mfc/reference/clistview-class.md), el marco de trabajo destruye el control cuando destruye la vista.  
  
 Si organiza para algunos de los datos de lista que se almacenará en la aplicación en lugar de con el control de lista, debe desasignarlos. Para obtener más información, consulte [elementos de devolución de llamada y la máscara de devolución de llamada](http://msdn.microsoft.com/library/windows/desktop/bb774736) en el SDK de Windows.  
  
 Además, es responsable de cancelar la asignación de las listas de imágenes creado y asociado con el objeto de control de lista.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

