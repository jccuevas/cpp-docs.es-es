---
title: Operaciones de portapapeles en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: e232010b443ace245844f1c28649477cccc8e9e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508961"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operaciones de portapapeles en los controles Rich Edit

La aplicación puede pegar el contenido del portapapeles en un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) con el mejor formato disponible del portapapeles o con un formato específico del portapapeles. También puede determinar si un control Rich Edit es capaz de pegar un formato de Portapapeles.

Puede copiar o cortar el contenido de la selección actual mediante la función miembro [copiar](../mfc/reference/cricheditctrl-class.md#copy) o [cortar](../mfc/reference/cricheditctrl-class.md#cut) . Del mismo modo, puede pegar el contenido del portapapeles en un control Rich Edit mediante la función miembro [Paste](../mfc/reference/cricheditctrl-class.md#paste) . El control pega el primer formato disponible que reconoce, lo que supuestamente es el formato más descriptivo.

Para pegar un formato específico del portapapeles, puede usar la función miembro [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) . Esta función es útil para las aplicaciones con un comando Pegar especial que permite al usuario seleccionar el formato del portapapeles. Puede usar la función miembro [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) para determinar si el control reconoce un formato determinado.

También puede usar `CanPaste` para determinar si un control de edición enriquecido reconoce cualquier formato de Portapapeles disponible. Esta función es útil en el `OnInitMenuPopup` controlador. Una aplicación podría habilitar o atenuar el comando pegar dependiendo de si el control puede pegar cualquier formato disponible.

Los controles Rich Edit registran dos formatos de portapapeles: el formato de texto enriquecido y un formato denominado texto y objetos de RichEdit. Una aplicación puede registrar estos formatos mediante la función [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) , especificando los valores **CF_RTF** y **CF_RETEXTOBJ** .

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
