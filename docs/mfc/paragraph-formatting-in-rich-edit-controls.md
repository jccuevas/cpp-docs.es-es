---
title: Formato de párrafo en los controles Rich Edit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8258ff95fc91f6f29d424e77be95ce1b44f621ac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215826"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit
Puede usar las funciones miembro de control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a párrafos y recuperar información de formato. Atributos de formato de párrafo incluyen la alineación, tabulaciones, las sangrías y numeración.  
  
 Puede aplicar formato mediante el uso de párrafo el [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) función miembro. Para determinar el formato del texto seleccionado de párrafo actual, use el [función miembro GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) función miembro. El [PARAFORMAT](/windows/desktop/api/richedit/ns-richedit-_paraformat) estructura se usa con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es *dwMask*. En `SetParaFormat`, *dwMask* especifica qué atributos de párrafo se establecen mediante esta llamada de función. `GetParaFormat` informa de los atributos del primer párrafo de la selección; *dwMask* especifica los atributos que son coherentes a lo largo de la selección.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

