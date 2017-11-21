---
title: 'Excepciones: Excepciones en los constructores | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0fb42a88c60b89909f104873ff20e36192b13c69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="exceptions-exceptions-in-constructors"></a>Excepciones: Excepciones en los constructores
Al iniciar una excepción en un constructor, limpiar los objetos y las asignaciones de memoria realizadas antes de iniciar la excepción, como se explica en [excepciones: iniciar excepciones desde sus propias funciones](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).  
  
 Al producir una excepción en un constructor, la memoria para el propio objeto ya se ha asignado en el momento en que se llama al constructor. Por lo tanto, el compilador desasignará automáticamente la memoria ocupada por el objeto después de que se produce la excepción.  
  
 Para obtener más información, consulte [excepciones: liberar objetos en excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

