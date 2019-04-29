---
title: Información de imágenes en las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: 7b83b7e5f7de6f8ccca95d732f71a5d73a97e943
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363523"
---
# <a name="image-information-in-image-lists"></a>Información de imágenes en las listas de imágenes

[CImageList](../mfc/reference/cimagelist-class.md) incluye una serie de funciones que recuperen información de una lista de imágenes. El [función miembro GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) rellena la función miembro un `IMAGEINFO` estructura con información acerca de una sola imagen, incluyendo los identificadores de los mapas de bits de imagen y la máscara, el número de planos de color y bits por píxel y el rectángulo delimitador de la imagen del mapa de bits de imagen. Puede usar esta información para manipular directamente los mapas de bits para la imagen.

El [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount) función miembro recupera el número de imágenes en una lista de imágenes.

Puede crear un icono basado en una imagen y una máscara en una lista de imágenes mediante la [función miembro ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) función miembro. La función devuelve el identificador del nuevo icono.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
