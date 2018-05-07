---
title: Comunicar con un Control de árbol | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af0b248d5e32b535c23cc17b48efdd551dad7a2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="communicating-with-a-tree-control"></a>Comunicar con un control de árbol
Usar varios métodos para llamar a funciones miembro un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto dependiendo de cómo se creó el objeto:  
  
-   Si el control de árbol está en un cuadro de diálogo, use una variable de miembro de tipo `CTreeCtrl` que se crean en la clase de cuadro de diálogo.  
  
-   Si el control de árbol es una ventana secundaria, use la `CTreeCtrl` objeto (o puntero) utiliza para construir el objeto.  
  
-   Si usas un `CTreeView` objeto, utilice la función [CTreeView:: GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) para obtener una referencia al control de árbol. Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un `CTreeCtrl` puntero.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

