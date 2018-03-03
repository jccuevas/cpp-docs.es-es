---
title: "Comunicar con un Control de árbol | Documentos de Microsoft"
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
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ef1188c9519e57c8132a2b20fc3b272d6c0ac51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="communicating-with-a-tree-control"></a>Comunicar con un control de árbol
Usar varios métodos para llamar a funciones miembro un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto dependiendo de cómo se creó el objeto:  
  
-   Si el control de árbol está en un cuadro de diálogo, use una variable de miembro de tipo `CTreeCtrl` que se crean en la clase de cuadro de diálogo.  
  
-   Si el control de árbol es una ventana secundaria, use la `CTreeCtrl` objeto (o puntero) utiliza para construir el objeto.  
  
-   Si usas un `CTreeView` objeto, utilice la función [CTreeView:: GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) para obtener una referencia al control de árbol. Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un `CTreeCtrl` puntero.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

