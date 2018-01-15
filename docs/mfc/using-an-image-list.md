---
title: "Usar una lista de imágenes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4321649bf4e8fe0e34fef8fe37b8c96598bef2c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

