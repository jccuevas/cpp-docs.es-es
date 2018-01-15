---
title: Usar CImageList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CImageList
dev_langs: C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 053e670b5a6d932c50e2f967ee38cf9191710ff4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-cimagelist"></a>Usar CImageList
Una lista de imágenes, representada por la clase [CImageList](../mfc/reference/cimagelist-class.md), es una colección de imágenes mismo tamaño, cada uno de los cuales puede hacer referencia por su índice. Listas de imágenes se utilizan para administrar eficazmente los grandes conjuntos de iconos o de mapas de bits. Listas de imágenes no son propiamente controles ya que no son windows; Sin embargo, se usan con distintos tipos de controles, incluyendo controles de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)), controles de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) y controles de fichas ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).  
  
 Todas las imágenes en una lista de imágenes están contenidas en un mapa de bits única y ancho, en formato de dispositivo de pantalla. Una lista de imágenes también puede incluir un mapa de bits monocromo que contenga máscaras utilizadas para dibujar imágenes de forma transparente (estilo de icono). `CImageList`proporciona funciones miembro que permiten dibujar imágenes, crear y destruir listas de imágenes, agregar y quitar imágenes, reemplazar imágenes, combinar imágenes y arrastrar imágenes.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Tipos de listas de imágenes](../mfc/types-of-image-lists.md)  
  
-   [Uso de una lista de imágenes](../mfc/using-an-image-list.md)  
  
-   [Manipulación de listas de imágenes](../mfc/manipulating-image-lists.md)  
  
-   [Dibujo de imágenes a partir de una lista de imágenes](../mfc/drawing-images-from-an-image-list.md)  
  
-   [Superposición de imágenes en las listas de imágenes](../mfc/image-overlays-in-image-lists.md)  
  
-   [Arrastre de imágenes de una lista de imágenes](../mfc/dragging-images-from-an-image-list.md)  
  
-   [Información de imágenes en las listas de imágenes](../mfc/image-information-in-image-lists.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles](../mfc/controls-mfc.md)

