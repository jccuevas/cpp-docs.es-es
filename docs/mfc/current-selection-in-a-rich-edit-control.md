---
title: Selección actual en un control Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 43a68d63f7888d762eee031196453eb156ecf105
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508768"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Selección actual en un control Rich Edit

El usuario puede seleccionar texto en un control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) mediante el mouse o el teclado. La selección actual es el intervalo de caracteres seleccionados o la posición del punto de inserción si no se selecciona ningún carácter. Una aplicación puede obtener información sobre la selección actual, establecer la selección actual, determinar cuándo cambia la selección actual y mostrar u ocultar el resaltado de la selección.

Para determinar la selección actual en un control Rich Edit, utilice la función miembro [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) . Para establecer la selección actual, utilice la función miembro [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) . La estructura [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) se utiliza con estas funciones para especificar un intervalo de caracteres. Para recuperar información sobre el contenido de la selección actual, puede usar la función miembro [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) .

De forma predeterminada, un control Rich Edit muestra y oculta el resaltado de la selección cuando gana y pierde el foco. Puede mostrar u ocultar el resaltado de la selección en cualquier momento mediante la función miembro [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) . Por ejemplo, una aplicación podría proporcionar un cuadro de diálogo de búsqueda para buscar texto en un control Rich Edit. La aplicación podría seleccionar texto coincidente sin cerrar el cuadro de diálogo, en cuyo caso debe usar `HideSelection` para resaltar la selección.

Para obtener el texto seleccionado en un control Rich Edit, utilice la función miembro [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) . El texto se copia en la matriz de caracteres especificada. Debe asegurarse de que la matriz es lo suficientemente grande como para contener el texto seleccionado más un carácter nulo de terminación.

Puede buscar una cadena en un control Rich Edit mediante el uso de la función miembro [FindText](../mfc/reference/cricheditctrl-class.md#findtext) la estructura [FINDTEXTEX](/windows/win32/api/richedit/ns-richedit-findtextexw) usada con esta función especifica el intervalo de texto que se va a buscar y la cadena que se va a buscar. También puede especificar estas opciones como si la búsqueda distinga entre mayúsculas y minúsculas.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
