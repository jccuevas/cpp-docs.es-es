---
title: Formato de párrafo en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: f2ac69838bf39afb636c3d41c97adc1378463d1b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507974"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit

Puede utilizar las funciones miembro del control Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a los párrafos y recuperar la información de formato. Los atributos de formato de párrafo incluyen alineación, tabulaciones, sangrías y numeración.

Puede aplicar formato de párrafo mediante la función miembro [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) . Para determinar el formato de párrafo actual del texto seleccionado, utilice la función miembro [GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) . La estructura [PARAFORMAT](/windows/win32/api/richedit/ns-richedit-paraformat) se utiliza con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es *dwMask*. En `SetParaFormat`, *dwMask* especifica qué atributos de párrafo se establecerán mediante esta llamada de función. `GetParaFormat`notifica los atributos del primer párrafo de la selección; *dwMask* especifica los atributos que son coherentes a lo largo de la selección.

## <a name="see-also"></a>Vea también

[Uso de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
