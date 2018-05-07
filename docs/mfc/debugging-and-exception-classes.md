---
title: Clases de excepciones y depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9adf6a585771336de9fb33abbebdd6bab97383ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-and-exception-classes"></a>Clases de excepciones y depuración
Estas clases proporcionan compatibilidad para la depuración de asignación de memoria dinámica y para pasar información de excepción de la función donde se produce la excepción a la función donde ésta se captura.  
  
 Utilizar clases [CDumpContext](../mfc/reference/cdumpcontext-class.md) y [CMemoryState](../mfc/reference/cmemorystate-structure.md) durante el desarrollo para ayudar con la depuración, como se describe en [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques). Use [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) para determinar la clase de cualquier objeto en tiempo de ejecución, como se describe en el artículo [acceso a información de clase de tiempo de ejecución](../mfc/accessing-run-time-class-information.md). El marco de trabajo usa `CRuntimeClass` para crear objetos de una clase determinada de forma dinámica.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

