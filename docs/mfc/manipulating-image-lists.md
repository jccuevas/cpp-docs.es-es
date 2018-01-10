---
title: "Manipular listas de imágenes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c2670f3935e2f4c482728000a268cb46cc9dbdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="manipulating-image-lists"></a>Manipular listas de imágenes
El [reemplazar](../mfc/reference/cimagelist-class.md#replace) función miembro reemplaza una imagen en una lista de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)) con una imagen nueva. Esta función también es útil si necesita aumentar dinámicamente el número de imágenes en un objeto de lista de imágenes. El [función SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) función cambia dinámicamente el número de imágenes almacenadas en la lista de imágenes. Si aumenta el tamaño de la lista de imágenes, llame a **reemplazar** para agregar imágenes a las ranuras de la imagen nueva. Si reduce el tamaño de la lista de imágenes, se liberan las imágenes que exceden el nuevo tamaño.  
  
 El [quitar](../mfc/reference/cimagelist-class.md#remove) función miembro quita una imagen de una lista de imágenes. El [copia](../mfc/reference/cimagelist-class.md#copy) función miembro puede copiar o intercambiar imágenes dentro de una lista de imágenes. Esta función permite indicar si se debe copiar la imagen de origen en el índice de destino o deben ajustarse las imágenes de origen y de destino.  
  
 Para crear una nueva lista de imágenes mediante la combinación de dos listas de imágenes, use la sobrecarga adecuada de la [crear](../mfc/reference/cimagelist-class.md#create) función miembro. Esta sobrecarga de **crear** combinaciones muestra la primera imagen de la imagen existente, almacenar la imagen resultante en un nuevo objeto de lista de imágenes. La nueva imagen se crea dibujando la segunda imagen transparente sobre la primera. La máscara de la nueva imagen es el resultado de realizar una operación OR lógica en los bits de las máscaras de las dos imágenes existentes.  
  
 Esto se repite hasta que todas las imágenes se combinan y se agregan al nuevo objeto de lista de imágenes.  
  
 Puede escribir la información de la imagen en un archivo mediante una llamada a la [escribir](../mfc/reference/cimagelist-class.md#write) función miembro y la lectura de nuevo mediante una llamada a la [lectura](../mfc/reference/cimagelist-class.md#read) función miembro.  
  
 El [funciones miembro GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [adjuntar](../mfc/reference/cimagelist-class.md#attach), y [separar](../mfc/reference/cimagelist-class.md#detach) funciones miembro permiten manipular el identificador de la lista de imágenes asociado a la `CImageList` objeto, mientras el [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) función miembro elimina la lista de imágenes sin destruir el `CImageList` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

