---
title: Formato de párrafo en los controles Rich Edit | Documentos de Microsoft
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
ms.openlocfilehash: 9417fe9bab9b1fca8ec8292e27efc02afec5511c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929152"
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit
Puede utilizar las funciones miembro de control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a párrafos y para recuperar información de formato. Atributos de formato de párrafo incluyen la alineación, tabuladores, sangría y numeración.  
  
 Puede aplicar formato mediante el uso de párrafo el [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) función miembro. Para determinar el formato para el texto seleccionado de párrafo actual, use la [función miembro GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) función miembro. El [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) estructura se utiliza con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es *dwMask*. En `SetParaFormat`, *dwMask* especifica qué atributos de párrafo se establecen mediante esta llamada a función. `GetParaFormat` informa de los atributos del primer párrafo de la selección; *dwMask* especifica los atributos que son coherentes en toda la selección.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

