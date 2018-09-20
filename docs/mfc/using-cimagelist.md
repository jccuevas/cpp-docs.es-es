---
title: Usar CImageList | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CImageList
dev_langs:
- C++
helpviewer_keywords:
- image list control
- CImageList class [MFC], using
ms.assetid: 3d2a909e-d641-46b7-aada-81cab1a29b41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ebfcb8fbacd3c464fc3697fc15bad385c1547d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420665"
---
# <a name="using-cimagelist"></a>Usar CImageList

Una lista de imágenes, representada por la clase [CImageList](../mfc/reference/cimagelist-class.md), es una colección de imágenes de un mismo tamaño, cada uno de los cuales se puede hacer referencia a por su índice. Listas de imágenes se usan para administrar eficazmente grandes conjuntos de iconos o mapas de bits. Listas de imágenes no son propiamente controles, ya que no son windows; Sin embargo, se usan con distintos tipos de controles, incluidos los controles de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)), controles de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) y controles de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)).

Todas las imágenes en una lista de imágenes se encuentran en un mapa de bits única y amplia en formato de dispositivo de pantalla. Una lista de imágenes también puede incluir un mapa de bits monocromo que contiene las máscaras utilizadas para dibujar imágenes de forma transparente (estilo de icono). `CImageList` proporciona funciones miembro que permiten dibujar imágenes, crear y destruir listas de imágenes, agregar y quitar imágenes, reemplazar imágenes, combinar imágenes y arrastrar imágenes.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Tipos de listas de imágenes](../mfc/types-of-image-lists.md)

- [Uso de una lista de imágenes](../mfc/using-an-image-list.md)

- [Manipulación de listas de imágenes](../mfc/manipulating-image-lists.md)

- [Dibujo de imágenes a partir de una lista de imágenes](../mfc/drawing-images-from-an-image-list.md)

- [Superposición de imágenes en las listas de imágenes](../mfc/image-overlays-in-image-lists.md)

- [Arrastre de imágenes de una lista de imágenes](../mfc/dragging-images-from-an-image-list.md)

- [Información de imágenes en las listas de imágenes](../mfc/image-information-in-image-lists.md)

## <a name="see-also"></a>Vea también

[Controles](../mfc/controls-mfc.md)

