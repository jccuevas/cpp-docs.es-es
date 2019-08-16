---
title: Clases relacionadas con controles Rich Edit
ms.date: 11/04/2016
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
ms.openlocfilehash: 349a8b5c26b7260c9af496d0f4a3a997ee753020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327241"
---
# <a name="classes-related-to-rich-edit-controls"></a>Clases relacionadas con controles Rich Edit

El [CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) clases proporcionan la funcionalidad del control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) en el contexto de la arquitectura documento/vista de MFC. `CRichEditView` mantiene el texto y la característica de formato de texto. `CRichEditDoc` mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem` proporciona acceso de contenedor para el elemento de cliente OLE. Para modificar el contenido de un `CRichEditView`, utilice [CRichEditView:: GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) para tener acceso a la base de control rich edit.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
