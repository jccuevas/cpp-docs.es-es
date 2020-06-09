---
title: Superposiciones de imágenes en las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: 861bcd5165ad0938ae6bbd77fc4a9f09095ce789
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624475"
---
# <a name="image-overlays-in-image-lists"></a>Superposiciones de imágenes en las listas de imágenes

Cada lista de imágenes ([CImageList](reference/cimagelist-class.md)) incluye una lista de imágenes que se van a usar como máscaras superpuestas. Una "máscara superpuesta" es una imagen dibujada de forma transparente sobre otra imagen. Cualquier imagen se puede usar como máscara de superposición. Puede especificar hasta cuatro máscaras superpuestas por lista de imágenes.

Agregue el índice de una imagen a la lista de máscaras de superposición mediante la función miembro [SetOverlayImage](reference/cimagelist-class.md#setoverlayimage) , el índice de una imagen y el índice de una máscara de superposición. Tenga en cuenta que los índices de las máscaras de superposición están basados en uno y no en cero.

Dibuje una máscara de superposición sobre una imagen mediante una sola llamada a `Draw` . Los parámetros incluyen el índice de la imagen que se va a dibujar y el índice de una máscara de superposición. Debe utilizar la macro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) para especificar el índice de la máscara de superposición. También puede especificar una imagen de superposición al llamar a la función miembro [DrawIndirect](reference/cimagelist-class.md#drawindirect) .

## <a name="see-also"></a>Consulte también

[Uso de CImageList](using-cimagelist.md)<br/>
[Permite](controls-mfc.md)
