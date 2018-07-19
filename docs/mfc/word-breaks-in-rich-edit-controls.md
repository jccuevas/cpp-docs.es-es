---
title: Separaciones de palabras en los controles Rich Edit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 373a30ed4a327cff99cb3cfce873707314608b57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382965"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Separaciones de palabras en los controles Rich Edit
Un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) llama a una función denominada "procedimiento de salto de palabra" para buscar saltos entre palabras y para determinar dónde se pueden romper líneas. El control utiliza esta información cuando se realizan operaciones de ajuste de palabras y al procesar las combinaciones de teclas CTRL+FLECHA izquierda y CTRL+FLECHA derecha. Una aplicación puede enviar mensajes a un control rich edit para reemplazar el procedimiento de separadores de palabras de forma predeterminada, para recuperar información de separadores de palabras y para determinar en qué línea de un carácter dado se encuentra.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

