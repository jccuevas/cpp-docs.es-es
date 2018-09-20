---
title: Información en listas de imágenes de la imagen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98bc629cde74cf7a6fc8a416de862f50a1dd5ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422290"
---
# <a name="image-information-in-image-lists"></a>Información de imágenes en las listas de imágenes

[CImageList](../mfc/reference/cimagelist-class.md) incluye una serie de funciones que recuperen información de una lista de imágenes. El [función miembro GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) rellena la función miembro un `IMAGEINFO` estructura con información acerca de una sola imagen, incluyendo los identificadores de los mapas de bits de imagen y la máscara, el número de planos de color y bits por píxel y el rectángulo delimitador de la imagen del mapa de bits de imagen. Puede usar esta información para manipular directamente los mapas de bits para la imagen.

El [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount) función miembro recupera el número de imágenes en una lista de imágenes.

Puede crear un icono basado en una imagen y una máscara en una lista de imágenes mediante la [función miembro ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) función miembro. La función devuelve el identificador del nuevo icono.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)

