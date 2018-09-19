---
title: Construcción de una fase y en dos fases de objetos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c53f99932887acad4d2eab5c15ed73b66b359fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346017"
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

