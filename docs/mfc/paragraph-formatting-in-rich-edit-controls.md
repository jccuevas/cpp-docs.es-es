---
title: Formato de párrafo en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: baee4863bee9b96e7a850e70b8f13388f69b41cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218837"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit

Puede usar las funciones miembro de control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a párrafos y recuperar información de formato. Atributos de formato de párrafo incluyen la alineación, tabulaciones, las sangrías y numeración.

Puede aplicar formato mediante el uso de párrafo el [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) función miembro. Para determinar el formato del texto seleccionado de párrafo actual, use el [función miembro GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) función miembro. El [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat) estructura se usa con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es *dwMask*. En `SetParaFormat`, *dwMask* especifica qué atributos de párrafo se establecen mediante esta llamada de función. `GetParaFormat` informa de los atributos del primer párrafo de la selección; *dwMask* especifica los atributos que son coherentes a lo largo de la selección.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
