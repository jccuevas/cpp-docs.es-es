---
title: Manipular listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
ms.openlocfilehash: cb7376241febd6bd1545cd183147e14a15313820
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622458"
---
# <a name="manipulating-image-lists"></a>Manipular listas de imágenes

La función miembro [Replace](reference/cimagelist-class.md#replace) reemplaza una imagen de una lista de imágenes ([CImageList](reference/cimagelist-class.md)) con una imagen nueva. Esta función también es útil si necesita aumentar dinámicamente el número de imágenes de un objeto de lista de imágenes. La función [SetImageCount](reference/cimagelist-class.md#setimagecount) cambia dinámicamente el número de imágenes almacenadas en la lista de imágenes. Si aumenta el tamaño de la lista de imágenes, llame `Replace` a para agregar imágenes a las nuevas ranuras de imagen. Si reduce el tamaño de la lista de imágenes, se liberan las imágenes que superen el tamaño nuevo.

La función miembro [Remove](reference/cimagelist-class.md#remove) quita una imagen de una lista de imágenes. La función miembro de [copia](reference/cimagelist-class.md#copy) puede copiar o intercambiar imágenes dentro de una lista de imágenes. Esta función le permite indicar si la imagen de origen se debe copiar en el índice de destino o se deben intercambiar las imágenes de origen y de destino.

Para crear una nueva lista de imágenes mediante la combinación de dos listas de imágenes, use la sobrecarga adecuada de la función miembro [Create](reference/cimagelist-class.md#create) . Esta sobrecarga de `Create` combina la primera imagen de las listas de imágenes existentes y almacena la imagen resultante en un nuevo objeto de lista de imágenes. La nueva imagen se crea dibujando la segunda imagen de forma transparente sobre la primera. La máscara de la nueva imagen es el resultado de realizar una operación OR lógica en los bits de las máscaras de las dos imágenes existentes.

Esto se repite hasta que todas las imágenes se combinan y se agregan al nuevo objeto de lista de imágenes.

Puede escribir la información de la imagen en un archivo mediante una llamada a la función miembro [Write](reference/cimagelist-class.md#write) y volver a leerla llamando a la función miembro [Read](reference/cimagelist-class.md#read) .

Las funciones miembro [GetSafeHandle](reference/cimagelist-class.md#getsafehandle), [Attach](reference/cimagelist-class.md#attach)y [detach](reference/cimagelist-class.md#detach) permiten manipular el identificador de la lista de imágenes asociada al `CImageList` objeto, mientras que la función miembro [DeleteImageList](reference/cimagelist-class.md#deleteimagelist) elimina la lista de imágenes sin destruir el `CImageList` objeto.

## <a name="see-also"></a>Consulte también

[Uso de CImageList](using-cimagelist.md)<br/>
[Permite](controls-mfc.md)
