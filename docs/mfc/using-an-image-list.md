---
title: Usar una lista de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: cb95de134939e1b06e2a8b827424c986f8c48ef3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293880"
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
