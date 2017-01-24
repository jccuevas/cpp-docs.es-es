---
title: "Usar CImageList | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CImageList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList (clase), utilizar"
  - "control de lista de imágenes"
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar CImageList
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una lista de imágenes, representada por la clase [CImageList](../mfc/reference/cimagelist-class.md), es una colección de imágenes mismo\- ordenadas, que se pueden hacer referencia por su índice.  Las listas de imágenes se utilizan para administrar eficazmente conjuntos grandes de iconos o de mapas de bits.  Las listas no son propios de imagen controles ya que no son ventanas; sin embargo, se utilizan varios tipos de controles, incluidos los controles de lista \([CListCtrl](../mfc/reference/clistctrl-class.md)\), los controles de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\), y los controles de ficha \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\).  
  
 Todas las imágenes en una lista de imágenes contenidas en un mapa de bits único, ancho en formato de PANT\- dispositivo.  Una lista de imágenes también puede incluir un mapa de bits monocromo que contiene las máscaras utilizadas para dibujar imágenes transparente \(estilo de icono\).  `CImageList` proporciona funciones miembro que permiten dibujar imágenes, crear o destruir listas de imágenes, para agregar y quitar imágenes, reemplazar imágenes, combinar, imágenes y arrastrar imágenes.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Tipos de listas de Imágenes](../mfc/types-of-image-lists.md)  
  
-   [Mediante una lista de Imágenes](../mfc/using-an-image-list.md)  
  
-   [Listas de manipulación de imágenes](../mfc/manipulating-image-lists.md)  
  
-   [Gráfico Imágenes de una lista de Imágenes](../mfc/drawing-images-from-an-image-list.md)  
  
-   [Se trata de la imagen en las listas de Imágenes](../mfc/image-overlays-in-image-lists.md)  
  
-   [Arrastrar Imágenes de una lista de Imágenes](../mfc/dragging-images-from-an-image-list.md)  
  
-   [Información de la imagen en las listas de Imágenes](../mfc/image-information-in-image-lists.md)  
  
## Vea también  
 [Controles](../mfc/controls-mfc.md)