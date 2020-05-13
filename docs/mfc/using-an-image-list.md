---
title: Usar una lista de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: 0d9566739a15e5d216eb052a7265313850515648
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366573"
---
# <a name="using-an-image-list"></a>Usar una lista de imágenes

El uso típico de una lista de imágenes sigue el siguiente patrón:

- Construir un [CImageList](../mfc/reference/cimagelist-class.md) objeto y llamar a [Create](../mfc/reference/cimagelist-class.md#create) una de las sobrecargas de `CImageList` su Create función para crear una lista de imágenes y adjuntarlo al objeto.

- Si no agregó imágenes al crear la lista de imágenes, agregue imágenes a la lista de imágenes llamando a la [función](../mfc/reference/cimagelist-class.md#add) miembro Agregar o [Leer.](../mfc/reference/cimagelist-class.md#read)

- Asocie la lista de imágenes con un control llamando a la función miembro adecuada de ese control o dibuje imágenes de la lista de imágenes usted mismo mediante la lista de imágenes [Draw](../mfc/reference/cimagelist-class.md#draw) función miembro.

- Tal vez permita al usuario arrastrar una imagen, utilizando la compatibilidad integrada de la lista de imágenes para arrastrar.

> [!NOTE]
> Si la lista de imágenes se creó con el **operador new,** debe destruir el `CImageList` objeto cuando haya terminado con él.

## <a name="see-also"></a>Consulte también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
