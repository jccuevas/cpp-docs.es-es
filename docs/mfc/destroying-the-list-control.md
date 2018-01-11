---
title: Destruir el Control de lista | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fdaafb8a6951050dac0022e0e6e8874b48d688e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-the-list-control"></a>Destruir el control de lista
Si incrusta el [CListCtrl](../mfc/reference/clistctrl-class.md) objeto como un miembro de datos de una clase de vista o cuadro de diálogo, se destruye cuando se destruye su propietario. Si utiliza un [CListView](../mfc/reference/clistview-class.md), el marco de trabajo destruye el control cuando destruye la vista.  
  
 Si organiza para algunos de los datos de lista que se almacenará en la aplicación en lugar de con el control de lista, debe desasignarlos. Para obtener más información, consulte [elementos de devolución de llamada y la máscara de devolución de llamada](http://msdn.microsoft.com/library/windows/desktop/bb774736) en el SDK de Windows.  
  
 Además, es responsable de cancelar la asignación de las listas de imágenes creado y asociado con el objeto de control de lista.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

