---
title: "Formato de párrafo en los controles Rich Edit | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rich edit controls [MFC], paragraph formatting in
- paragraph formatting in CRichEditCtrl [MFC]
- CRichEditCtrl class [MFC], paragraph formatting in
- formatting [MFC], paragraphs
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f0dc12d923f6f424fe84768b0d934d8dd7ff20b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="paragraph-formatting-in-rich-edit-controls"></a>Formato de párrafo en los controles Rich Edit
Puede utilizar las funciones miembro de control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) para dar formato a párrafos y para recuperar información de formato. Atributos de formato de párrafo incluyen la alineación, tabuladores, sangría y numeración.  
  
 Puede aplicar formato mediante el uso de párrafo el [SetParaFormat](../mfc/reference/cricheditctrl-class.md#setparaformat) función miembro. Para determinar el formato para el texto seleccionado de párrafo actual, use la [función miembro GetParaFormat](../mfc/reference/cricheditctrl-class.md#getparaformat) función miembro. El [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) estructura se utiliza con estas funciones miembro para especificar atributos de párrafo. Uno de los miembros importantes de **PARAFORMAT** es **dwMask**. En `SetParaFormat`, **dwMask** especifica qué atributos de párrafo se establecen mediante esta llamada a función. `GetParaFormat`informa de los atributos del primer párrafo de la selección; **dwMask** especifica los atributos que son coherentes en toda la selección.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)
