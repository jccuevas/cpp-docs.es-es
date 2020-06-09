---
title: Información de imágenes en las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: c12198c769585763095d22b73d11f7af3c9d6fc0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624500"
---
# <a name="image-information-in-image-lists"></a>Información de imágenes en las listas de imágenes

[CImageList](reference/cimagelist-class.md) incluye varias funciones que recuperan información de una lista de imágenes. La función miembro [GetImageInfo](reference/cimagelist-class.md#getimageinfo) rellena una `IMAGEINFO` estructura con información sobre una sola imagen, incluidos los identificadores de los mapas de bits de la imagen y la máscara, el número de planos de color y los bits por píxel, y el rectángulo delimitador de la imagen dentro del mapa de bits de la imagen. Puede usar esta información para manipular directamente los mapas de bits de la imagen.

La función miembro [GetImageCount](reference/cimagelist-class.md#getimagecount) recupera el número de imágenes de una lista de imágenes.

Puede crear un icono basado en una imagen y una máscara en una lista de imágenes mediante la función miembro [ExtractIcon](reference/cimagelist-class.md#extracticon) . La función devuelve el identificador del nuevo icono.

## <a name="see-also"></a>Consulte también

[Uso de CImageList](using-cimagelist.md)<br/>
[Permite](controls-mfc.md)
