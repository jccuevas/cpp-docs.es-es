---
title: Separaciones de palabras en los controles Rich Edit | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12ae5d682515a6f266b7e41a2ff89148ea98c0b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="word-breaks-in-rich-edit-controls"></a>Separaciones de palabras en los controles Rich Edit
Un control rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) llama a una función denominada "procedimiento de salto de palabra" para buscar saltos entre palabras y para determinar dónde se pueden romper líneas. El control utiliza esta información cuando se realizan operaciones de ajuste de palabras y al procesar las combinaciones de teclas CTRL+FLECHA izquierda y CTRL+FLECHA derecha. Una aplicación puede enviar mensajes a un control rich edit para reemplazar el procedimiento de separadores de palabras de forma predeterminada, para recuperar información de separadores de palabras y para determinar en qué línea de un carácter dado se encuentra.  
  
## <a name="see-also"></a>Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)

