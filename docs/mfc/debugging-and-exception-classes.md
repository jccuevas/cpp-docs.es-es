---
title: Clases de excepciones y depuración | Microsoft Docs
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
ms.openlocfilehash: 4b7c88c5d12f56318bbb37a825e28c2bfcbc132d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418182"
---
# <a name="debugging-and-exception-classes"></a>Clases de excepciones y depuración

Estas clases proporcionan compatibilidad para la depuración de asignación de memoria dinámica y para pasar información de excepción de la función donde se produjo la excepción a la función donde se detecta.

Utilizar clases [CDumpContext](../mfc/reference/cdumpcontext-class.md) y [CMemoryState](../mfc/reference/cmemorystate-structure.md) durante el desarrollo para ayudar con la depuración, como se describe en [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques). Use [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) para determinar la clase de cualquier objeto en tiempo de ejecución, como se describe en el artículo [acceso a información de clase de tiempo de ejecución](../mfc/accessing-run-time-class-information.md). El marco usa `CRuntimeClass` para crear objetos de una clase determinada de forma dinámica.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

