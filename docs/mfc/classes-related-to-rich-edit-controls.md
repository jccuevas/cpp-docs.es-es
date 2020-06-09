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
ms.openlocfilehash: 584649a2bb2d9a118e390aebf9f7411c3123b1a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620710"
---
# <a name="classes-related-to-rich-edit-controls"></a>Clases relacionadas con controles Rich Edit

Las clases [CRichEditView](reference/cricheditview-class.md), [CRichEditDoc](reference/cricheditdoc-class.md)y [CRichEditCntrItem](reference/cricheditcntritem-class.md) proporcionan la funcionalidad del control Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) en el contexto de la arquitectura de documento/vista de MFC. `CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso de contenedor al elemento de cliente OLE. Para modificar el contenido de un `CRichEditView` , utilice [CRichEditView:: GetRichEditCtrl](reference/cricheditview-class.md#getricheditctrl) para tener acceso al control Rich Edit subyacente.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Permite](controls-mfc.md)
