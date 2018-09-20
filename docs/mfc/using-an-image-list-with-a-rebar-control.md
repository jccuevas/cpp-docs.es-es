---
title: Uso de una lista de imágenes con un Control Rebar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff524f1f29e4db2ac5bb4628064583f0fe7583e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372371"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Usar una lista de imágenes con un control Rebar

Cada banda rebar puede contener, entre otras cosas, una imagen de una lista de imágenes asociado. El siguiente procedimiento detalla los pasos necesarios para mostrar una imagen en una banda rebar.

### <a name="to-display-images-in-a-rebar-band"></a>Para mostrar imágenes en una banda rebar

1. Asociar una lista de imágenes a su objeto de control rebar mediante una llamada a [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), pasando un puntero a una lista de imágenes existente.

1. Modificar el **REBARBANDINFO** estructura para asignar una imagen a una banda rebar:

   - Establecer el *fMask* miembro `RBBIM_IMAGE`, usando el operador OR bit a bit para incluir marcas adicionales según sea necesario.

   - Establecer el *iImage* miembro para el índice de la lista de imágenes de la imagen que se mostrará.

1. Inicializar a los miembros de datos restantes, como el tamaño, el texto y el identificador de la ventana secundaria contenida, con la información necesaria.

1. Inserte la nueva banda (con la imagen) con una llamada a [CReBarCtrl:: InsertBand](../mfc/reference/crebarctrl-class.md#insertband), pasando el **REBARBANDINFO** estructura.

El siguiente ejemplo se supone que un objeto de lista de imágenes existente con dos imágenes se adjunta al objeto de control rebar (`m_wndReBar`). Una banda rebar (definida por `rbi`), que contiene la primera imagen, se agrega con una llamada a `InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

