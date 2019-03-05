---
title: Selección actual en un control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 4516c4506419169ac3ab284e6c59cae71595be59
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286869"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Selección actual en un control Rich Edit

El usuario puede seleccionar texto en un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) mediante el mouse o el teclado. La selección actual es el intervalo de caracteres seleccionados, o la posición del punto de inserción si no hay caracteres están seleccionadas. Una aplicación puede obtener información acerca de la selección actual, establezca la selección actual, determinar cuándo resaltar los cambios de selección actual y mostrar u ocultar la selección.

Para determinar la selección actual en un control rich edit, utilice la [función miembro GetSel](../mfc/reference/cricheditctrl-class.md#getsel) función miembro. Para establecer la selección actual, utilice el [función miembro SetSel](../mfc/reference/cricheditctrl-class.md#setsel) función miembro. El [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) estructura se usa con estas funciones para especificar un intervalo de caracteres. Para recuperar información sobre el contenido de la selección actual, se puede utilizar el [función miembro GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) función miembro.

De forma predeterminada, un control rich edit muestra y oculta el área resaltada de selección cuando recibe y pierde el foco. Puede mostrar u ocultar resaltado de la selección en cualquier momento mediante el [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) función miembro. Por ejemplo, una aplicación podría proporcionar un cuadro de diálogo de búsqueda para buscar texto en un control rich edit. La aplicación podría seleccionar el texto coincidente sin cerrar el cuadro de diálogo, en cuyo caso debe usar `HideSelection` para resaltar la selección.

Para obtener el texto seleccionado en un control rich edit, use el [función miembro GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) función miembro. El texto se copia en la matriz de caracteres especificada. Debe asegurarse de que la matriz es lo suficientemente grande como para contener el texto seleccionado más de un carácter nulo de terminación.

Puede buscar una cadena en un control rich edit mediante el [FindText](../mfc/reference/cricheditctrl-class.md#findtext) función miembro el [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa) estructura utilizada con esta función especifica el intervalo de texto de búsqueda y la cadena de búsqueda. También puede especificar opciones tales como la búsqueda no distingue entre mayúsculas y minúsculas.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
