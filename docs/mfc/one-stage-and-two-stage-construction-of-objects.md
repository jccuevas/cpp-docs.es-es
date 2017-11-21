---
title: "Construcción de una fase y en dos fases de objetos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f3e337f96c1acef53b1ec34237d31a868fb4dfe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construcción de objetos en una fase y en dos fases
Tendrá que elegir entre dos técnicas para crear objetos gráficos, como lápices y pinceles:  
  
-   *Construcción de una fase*: se crea e inicializa el objeto en una fase, todo ello con el constructor.  
  
-   *Construcción en dos fases*: se crea e inicializa el objeto en dos fases independientes. El constructor crea el objeto y una función de inicialización lo inicializa.  
  
 Construcción en dos fases siempre es más seguro. En la construcción de una fase, el constructor podría producir una excepción si se proporcionan argumentos incorrectos o se produce un error en la asignación de memoria. Este problema se evita por construcción en dos fases, aunque tiene comprobación de errores. En cualquier caso, destruye el objeto es el mismo proceso.  
  
> [!NOTE]
>  Estas técnicas se aplican a la creación de los objetos, no sólo de objetos gráficos.  
  
## <a name="example-of-both-construction-techniques"></a>Ejemplo de ambas técnicas de construcción  
 En el siguiente ejemplo muestra ambos métodos de creación de un objeto de lápiz:  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Objetos gráficos](../mfc/graphic-objects.md)  
  
-   [Seleccionar un objeto gráfico en un contexto de dispositivo](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Dibujo en una vista](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Vea también  
 [Objetos gráficos](../mfc/graphic-objects.md)

