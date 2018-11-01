---
title: Usar una lista de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: fb0636d29d5bf72007eb440f763de0d5e1f4b581
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581251"
---
# <a name="using-an-image-list"></a>Usar una lista de imágenes

Uso típico de una lista de imágenes sigue el patrón siguiente:

- Construir un [CImageList](../mfc/reference/cimagelist-class.md) de objetos y llamar a una de las sobrecargas de su [crear](../mfc/reference/cimagelist-class.md#create) función para crear una lista de imágenes y adjuntarla a la `CImageList` objeto.

- Si no ha agregado imágenes al crear la lista de imágenes, agregar imágenes a la lista de imágenes mediante una llamada a la [agregar](../mfc/reference/cimagelist-class.md#add) o [lectura](../mfc/reference/cimagelist-class.md#read) función miembro.

- Asociar la lista de imágenes con un control mediante una llamada a la función miembro adecuado de ese control, o dibujar imágenes desde la lista de imágenes mediante la lista de imágenes [dibujar](../mfc/reference/cimagelist-class.md#draw) función miembro.

- Quizás permite al usuario arrastrar una imagen, con compatibilidad integrada con la lista de imágenes para arrastrar.

> [!NOTE]
>  Si se creó la lista de imágenes con el **nueva** (operador), deberá destruir la `CImageList` objeto cuando haya terminado con él.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)

