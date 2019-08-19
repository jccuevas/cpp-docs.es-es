---
title: Formato de párrafo en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: 0988e7940c8d8947b86e97a35d71586f8f5c316a
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916376"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit

Puede utilizar las funciones miembro del control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a los párrafos y recuperar la información de formato. Los atributos de formato de párrafo incluyen alineación, tabulaciones, sangrías y numeración.

Puede aplicar formato de párrafo mediante la función miembro [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) . Para determinar el formato de párrafo actual del texto seleccionado, utilice la función miembro [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) . La estructura [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-paraformat) se utiliza con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es *dwMask*. En `SetParaFormat`, *dwMask* especifica qué atributos de párrafo se establecerán mediante esta llamada de función. `GetParaFormat`notifica los atributos del primer párrafo de la selección; *dwMask* especifica los atributos que son coherentes a lo largo de la selección.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
