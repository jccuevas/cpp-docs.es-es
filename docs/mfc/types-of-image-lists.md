---
title: Tipos de listas de imágenes | Microsoft Docs
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
ms.openlocfilehash: 3bea24d487170ea4cac470f2244340f6b570d1ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390479"
---
# <a name="types-of-image-lists"></a>Tipos de listas de imágenes

Hay dos tipos de listas de imágenes ([CImageList](../mfc/reference/cimagelist-class.md)): no enmascaradas y enmascaradas. Una "lista de imágenes no enmascarada" consta de un mapa de bits de color que contiene una o varias imágenes. Una "lista de imágenes enmascarada" consta de dos mapas de bits del mismo tamaño. El primero es un mapa de bits de color que contiene las imágenes y el segundo es un mapa de bits monocromo que contiene una serie de máscaras, uno para cada imagen de mapa de bits primero.

Una de las sobrecargas de los `Create` función miembro toma una marca para indicar si la lista de imágenes está enmascarada. (Las otras sobrecargas crean listas de imágenes con máscara.)

Cuando se dibuja una imagen no enmascarada, simplemente se copian en el contexto de dispositivo de destino; es decir, se dibuja con el color de fondo existente del contexto del dispositivo. Cuando se dibuja una imagen enmascarada, los bits de la imagen se combinan con los bits de la máscara, produciendo normalmente áreas transparentes del mapa de bits donde se muestra el color de fondo del contexto de dispositivo de destino a través. Puede especificar varios estilos de dibujo al dibujar una imagen enmascarada. Por ejemplo, puede especificar que la imagen esté interpolada para indicar un objeto seleccionado.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)

