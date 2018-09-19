---
title: ¿Tengo que derivar las clases nuevas de CObject? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51904ac06ae6c2db5586f8dc405f85145c5b1f30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343065"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>¿Tengo que derivar las clases nuevas de CObject?
No, no es necesario.  
  
 Derivar una clase de [CObject](../mfc/reference/cobject-class.md) cuando necesite las funciones que ofrece, como la serialización o CObject dinámica. Muchas clases de datos deban serializarse a archivos, por lo que a menudo es una buena idea para derivar desde `CObject`. Para un ejemplo de una clase derivada de `CObject`, consulte el [ejemplo Scribble](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
