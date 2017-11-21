---
title: "Tipos de listas de imágenes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 430bc574fdb35fca08dcbe3a3ea503f809d08985
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="types-of-image-lists"></a>Tipos de listas de imágenes
Hay dos tipos de listas de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)): no enmascaradas y enmascaradas. Una "lista de imágenes no enmascarada" se compone de un mapa de bits de color que contiene una o más imágenes. Una "lista de imágenes enmascarada" se compone de dos mapas de bits del mismo tamaño. El primero es un mapa de bits de color que contiene las imágenes y el segundo es un mapa de bits monocromo que contiene una serie de máscaras: uno para cada imagen del primer mapa de bits.  
  
 Una de las sobrecargas de la **crear** función miembro toma una marca para indicar si la lista de imágenes se enmascara. (Las otras sobrecargas crean listas de imágenes enmascaradas.)  
  
 Cuando se dibuja una imagen no enmascarada, simplemente se copian en el contexto de dispositivo de destino; es decir, se dibuja en el color de fondo existente del contexto del dispositivo. Cuando se dibuja una imagen enmascarada, los bits de la imagen se combinan con los bits de la máscara, produciendo normalmente áreas transparentes del mapa de bits donde se muestra el color de fondo del contexto de dispositivo de destino a través de. Puede especificar varios estilos de dibujo al dibujar una imagen enmascarada. Por ejemplo, puede especificar que la imagen esté interpolada para indicar un objeto seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

