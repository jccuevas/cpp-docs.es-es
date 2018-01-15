---
title: "¿Tengo que derivar las clases nuevas de CObject? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CObject
dev_langs: C++
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c485bba4d62d279b0f17b887080284940a8bbdd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>¿Tengo que derivar las clases nuevas de CObject?
No, no es necesario.  
  
 Derivar una clase de [CObject](../mfc/reference/cobject-class.md) cuando necesite las funciones que ofrece, como la serialización o CObject dinámica. Muchas clases de datos deban serializarse a archivos, por lo que a menudo es una buena idea para derivar desde `CObject`. Para un ejemplo de una clase derivada de `CObject`, consulte el [ejemplo Scribble](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
