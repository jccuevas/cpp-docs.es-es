---
title: 'TN032: Mecanismo de excepciones de MFC | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.exceptions
dev_langs: C++
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf82d4b158cedd2d8f6916dfb01d26db6c62d83b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Mecanismo de excepciones de MFC
Las versiones anteriores de Visual C++ no admitía el mecanismo de excepción estándar de C++ y MFC proporciona macros **TRY/CATCH y THROW** empleadas en su lugar. Esta versión de Visual C++ es totalmente compatible con las excepciones de C++. Esta nota trata algunos de los detalles de implementación avanzada de las macros anteriores e incluye información para objetos de pila en función de limpieza automáticamente. Dado que las excepciones de C++ admiten pila desenredo de forma predeterminada, esta nota técnica ya no es necesaria.  
  
 Hacer referencia a [excepciones: utilizar Macros de MFC y las excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) para obtener más información sobre las diferencias entre las macros MFC y las nuevas palabras clave de C++.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

