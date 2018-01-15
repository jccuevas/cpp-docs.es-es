---
title: "La imagen se superpone en listas de imágenes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e70365040b5f009e634a4867a4a1f974d47bd61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="image-overlays-in-image-lists"></a>Superposiciones de imágenes en las listas de imágenes
Cada lista de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)) incluye una lista de imágenes que se utilizan como máscaras superpuestas. Una "máscara superpuesta" es una imagen dibujada de forma transparente sobre otra imagen. Cualquier imagen puede usarse como una máscara superpuesta. Puede especificar hasta cuatro máscaras superpuestas por lista de imágenes.  
  
 Agregue el índice de una imagen a la lista de máscaras superpuestas utilizando la [función miembro SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) función miembro, el índice de una imagen y el índice de una máscara superpuesta. Tenga en cuenta que los índices de las máscaras superpuestas basado en uno, en lugar de base cero.  
  
 Dibuja una máscara superpuesta sobre una imagen con una sola llamada a **dibujar**. Los parámetros incluyen el índice de la imagen para dibujar y el índice de una máscara superpuesta. Debe utilizar el [macro INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) macro para especificar el índice de la máscara de superposición. También puede especificar una imagen superpuesta al llamar a la [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

