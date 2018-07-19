---
title: Dibujar imágenes a partir de una lista de imágenes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ebc05a83eb22d494a75ed474e315112522af3fc
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932073"
---
# <a name="drawing-images-from-an-image-list"></a>Dibujar imágenes a partir de una lista de imágenes
Para dibujar una imagen, utilice la [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) función miembro. Especificará un puntero a un objeto de contexto de dispositivo, el índice de la imagen para dibujar, la ubicación en el contexto de dispositivo en el que se va a dibujar la imagen y un conjunto de indicadores para indicar el estilo de dibujo.  
  
 Cuando se especifica la **ILD_TRANSPARENT** estilo, `Draw` usa un proceso de dos pasos para dibujar una imagen enmascarada. En primer lugar, realiza una operación lógica- y operación en los bits de la imagen y los bits de la máscara. A continuación, realiza una operación XOR lógico en los resultados de la primera operación y los bits de fondo del contexto de dispositivo de destino. Este proceso crea las áreas transparentes en la imagen resultante; es decir, cada bit en blanco en la máscara hace que el bit correspondiente de la imagen resultante sea transparente.  
  
 Antes de dibujar una imagen enmascarada sobre un fondo de color sólido, debe utilizar el [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) función de miembro para establecer el color de fondo de la lista de imágenes en el mismo color que el destino. Establecer el color elimina la necesidad de crear las áreas transparentes en la imagen y permite `Draw` simplemente copiar la imagen en el contexto de dispositivo de destino, lo que produce un aumento significativo del rendimiento. Para dibujar la imagen, especifique la **ILD_NORMAL** aplicar estilo al llamar a `Draw`.  
  
 Puede establecer el color de fondo para obtener una lista de imágenes enmascarada ([CImageList](../mfc/reference/cimagelist-class.md)) en cualquier momento, por lo que se dibuja correctamente en cualquier fondo sólido. Si se establece el color de fondo en **como CLR_NONE** hace imágenes se dibujan de forma transparente de forma predeterminada. Para recuperar el color de fondo de una lista de imágenes, use la [función miembro GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) función miembro.  
  
 El **ILD_BLEND25** y **ILD_BLEND50** estilos interpolación la imagen con el color de resaltado del sistema. Estos estilos son útiles si utiliza una imagen enmascarada para representar un objeto que el usuario puede seleccionar. Por ejemplo, puede usar el **ILD_BLEND50** estilo que se va a dibujar la imagen cuando el usuario lo selecciona.  
  
 Una imagen no enmascarada se copia en el contexto de dispositivo de destino mediante el `SRCCOPY` operación de trama. Los colores de la imagen aparecen los mismos, independientemente del color de fondo del contexto de dispositivo. Los estilos de dibujo especificados en `Draw` tampoco tienen ningún efecto en la apariencia de una imagen no enmascarada.  
  
 Además de la función miembro Draw, otra función, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), amplía la capacidad para representar una imagen. `DrawIndirect` toma como parámetro, un [estructura IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) estructura. Esta estructura se puede utilizar para personalizar la representación de la imagen actual, incluido el uso de los códigos de operación (ROP) de trama. Para obtener más información sobre códigos ROP, vea [los códigos de operación de trama](http://msdn.microsoft.com/library/windows/desktop/dd162892) y [mapas de bis como pinceles](http://msdn.microsoft.com/library/windows/desktop/dd183378) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

