---
title: CTreeCtrl frente a CTreeView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs: C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5a0dfd4f7b658cc585972ace1335a80b9bbd93a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl frente a CTreeView
MFC proporciona dos clases que encapsulan los controles de árbol: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md). Cada clase es útil en situaciones diferentes.  
  
 Utilice `CTreeCtrl` cuando se necesita un control de ventana secundaria plana; por ejemplo, en un cuadro de diálogo. Especialmente desearía utilizar `CTreeCtrl` si va a haber más controles secundarios en la ventana, como se muestra en un cuadro de diálogo típico.  
  
 Use `CTreeView` si desea que el control de árbol para que actúe como una ventana de vista en la arquitectura documento/vista, así como un control de árbol. Un `CTreeView` ocupan toda el área cliente de una ventana de marco o una ventana divisora. Se cambiará automáticamente de tamaño cuando se cambia el tamaño de su ventana primaria y puede procesar mensajes de comandos de menús, teclas de aceleración y barras de herramientas. Puesto que un control de árbol contiene los datos necesarios para mostrar el árbol, el objeto de documento correspondiente no tiene que ser complicado, puede usar incluso [CDocument](../mfc/reference/cdocument-class.md) como el tipo de documento en la plantilla de documento.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)
