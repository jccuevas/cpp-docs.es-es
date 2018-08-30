---
title: La imagen se superpone en listas de imágenes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4369fe312669f75eb8217be7a6a09c4287f7cc8b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210718"
---
# <a name="image-overlays-in-image-lists"></a>Superposiciones de imágenes en las listas de imágenes
Cada lista de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)) incluye una lista de imágenes que puede usar como máscaras de superposición. Una "máscara superpuesta" es una imagen dibujada de forma transparente sobre otra imagen. Puede utilizarse cualquier imagen como máscara de superposición. Puede especificar hasta cuatro máscaras superpuestas por lista de imágenes.  
  
 Agregue el índice de una imagen a la lista de máscaras superpuestas utilizando la [función miembro SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) función miembro, el índice de una imagen y el índice de una máscara de superposición. Tenga en cuenta que los índices de las máscaras de superposición son basado en uno en lugar de base cero.  
  
 Dibujar una máscara superpuesta a través de una imagen mediante una sola llamada a `Draw`. Los parámetros incluyen el índice de la imagen para dibujar y el índice de una máscara de superposición. Debe usar el [macro INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro para especificar el índice de la máscara de superposición. También puede especificar una imagen de superposición al llamar a la [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

