---
title: Clases relacionadas con controles Rich Edit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f428242ac84adaf36ea0263f8e193dfeca7d0609
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="classes-related-to-rich-edit-controls"></a>Clases relacionadas con controles Rich Edit
El [CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) clases proporcionan la funcionalidad del control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) en el contexto de la arquitectura documento/vista de MFC. `CRichEditView` mantiene el texto y la característica de formato de texto. `CRichEditDoc` mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem` proporciona acceso de contenedor para el elemento de cliente OLE. Para modificar el contenido de un `CRichEditView`, use [CRichEditView:: GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) para tener acceso a subyacente control rich edit.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

