---
title: Manipular listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: 1e86961980c91ade47a3d6510dec5c04ac36cffb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304852"
---
# <a name="manipulating-image-lists"></a>Manipular listas de imágenes

El [reemplazar](../mfc/reference/cimagelist-class.md#replace) función miembro reemplaza una imagen en una lista de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)) con una imagen nueva. Esta función también es útil si necesita aumentar dinámicamente el número de imágenes en un objeto de lista de imágenes. El [función SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) función cambia dinámicamente el número de imágenes almacenadas en la lista de imágenes. Si aumenta el tamaño de la lista de imágenes, llame a `Replace` agregar imágenes a las ranuras de la imagen nueva. Si disminuye el tamaño de la lista de imágenes, se liberan las imágenes más allá del tamaño nuevo.

El [quitar](../mfc/reference/cimagelist-class.md#remove) función miembro quita una imagen de una lista de imágenes. El [copia](../mfc/reference/cimagelist-class.md#copy) función miembro puede copiar o intercambiar imágenes dentro de una lista de imágenes. Esta función permite indicar si la imagen de origen debe copiarse en el índice de destino o deben ajustarse las imágenes de origen y destino.

Para crear una lista de imágenes mediante la combinación de dos listas de imágenes, use la sobrecarga adecuada del [crear](../mfc/reference/cimagelist-class.md#create) función miembro. Esta sobrecarga de `Create` combinaciones muestra la primera imagen de la imagen existente, almacenar la imagen resultante en un nuevo objeto de lista de imágenes. La nueva imagen se crea mediante el dibujo de forma transparente la segunda imagen a través de la primera. La máscara de la imagen nueva es el resultado de realizar una operación OR lógica de los bits de las máscaras de las dos imágenes existentes.

Esto se repite hasta que todas las imágenes se combinan y se agregan al nuevo objeto de lista de imágenes.

Puede escribir la información de la imagen en un archivo mediante una llamada a la [escribir](../mfc/reference/cimagelist-class.md#write) función miembro y mediante una llamada a volver a leerlos los [lectura](../mfc/reference/cimagelist-class.md#read) función miembro.

El [funciones miembro GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [adjuntar](../mfc/reference/cimagelist-class.md#attach), y [Detach](../mfc/reference/cimagelist-class.md#detach) funciones miembro permiten manipular el identificador de la lista de imágenes asociado a la `CImageList` objeto, mientras que el [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) función miembro elimina la lista de imágenes sin destruir el `CImageList` objeto.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
