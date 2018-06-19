---
title: Tipos de listas de imágenes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8988dc55bbbaa1d446ee14bf78a0cd799b422834
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385890"
---
# <a name="types-of-image-lists"></a>Tipos de listas de imágenes
Hay dos tipos de listas de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)): no enmascaradas y enmascaradas. Una "lista de imágenes no enmascarada" se compone de un mapa de bits de color que contiene una o más imágenes. Una "lista de imágenes enmascarada" se compone de dos mapas de bits del mismo tamaño. El primero es un mapa de bits de color que contiene las imágenes y el segundo es un mapa de bits monocromo que contiene una serie de máscaras: uno para cada imagen del primer mapa de bits.  
  
 Una de las sobrecargas de la **crear** función miembro toma una marca para indicar si la lista de imágenes se enmascara. (Las otras sobrecargas crean listas de imágenes enmascaradas.)  
  
 Cuando se dibuja una imagen no enmascarada, simplemente se copian en el contexto de dispositivo de destino; es decir, se dibuja en el color de fondo existente del contexto del dispositivo. Cuando se dibuja una imagen enmascarada, los bits de la imagen se combinan con los bits de la máscara, produciendo normalmente áreas transparentes del mapa de bits donde se muestra el color de fondo del contexto de dispositivo de destino a través de. Puede especificar varios estilos de dibujo al dibujar una imagen enmascarada. Por ejemplo, puede especificar que la imagen esté interpolada para indicar un objeto seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

