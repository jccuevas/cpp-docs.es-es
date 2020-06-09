---
title: Formato de párrafo en los controles Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
ms.openlocfilehash: e23976e64b3c9a4a76e5b05c90d0ad033b62657a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615333"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit

Puede utilizar las funciones miembro del control Rich Edit ([CRichEditCtrl](reference/cricheditctrl-class.md)) para dar formato a los párrafos y recuperar la información de formato. Los atributos de formato de párrafo incluyen alineación, tabulaciones, sangrías y numeración.

Puede aplicar formato de párrafo mediante la función miembro [SetParaFormat](reference/cricheditctrl-class.md#setparaformat) . Para determinar el formato de párrafo actual del texto seleccionado, utilice la función miembro [GetParaFormat](reference/cricheditctrl-class.md#getparaformat) . La estructura [PARAFORMAT](/windows/win32/api/richedit/ns-richedit-paraformat) se utiliza con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es *dwMask*. En `SetParaFormat` , *dwMask* especifica qué atributos de párrafo se establecerán mediante esta llamada de función. `GetParaFormat`notifica los atributos del primer párrafo de la selección; *dwMask* especifica los atributos que son coherentes a lo largo de la selección.

## <a name="see-also"></a>Consulte también

[Uso de CRichEditCtrl](using-cricheditctrl.md)<br/>
[Permite](controls-mfc.md)
