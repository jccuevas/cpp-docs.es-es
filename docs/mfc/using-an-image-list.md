---
title: Usar una lista de imágenes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5722a2ef8c4e93e4996ee243b3c01b6dd6aeca78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-image-list"></a>Usar una lista de imágenes
Uso típico de una lista de imágenes sigue el modelo siguiente:  
  
-   Construir un [CImageList](../mfc/reference/cimagelist-class.md) objeto y llamar a una de las sobrecargas de su [crear](../mfc/reference/cimagelist-class.md#create) función para crear una lista de imágenes y adjuntarla a la `CImageList` objeto.  
  
-   Si no ha agregado imágenes al crear la lista de imágenes, agregar imágenes a la lista de imágenes mediante una llamada a la [agregar](../mfc/reference/cimagelist-class.md#add) o [lectura](../mfc/reference/cimagelist-class.md#read) función miembro.  
  
-   Asociar la lista de imágenes con un control mediante una llamada a la función miembro adecuado de ese control, o dibujar imágenes desde la lista de imágenes mediante la lista de imágenes [dibujar](../mfc/reference/cimagelist-class.md#draw) función miembro.  
  
-   Quizás permite al usuario arrastrar una imagen, con compatibilidad integrada con la lista de imágenes para arrastrar.  
  
> [!NOTE]
>  Si se creó la lista de imágenes con la **nueva** (operador), deberá destruir la `CImageList` objeto cuando haya terminado con él.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

