---
title: Usar una lista de imágenes con un control Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: fa5307c201850fc42439c79a1c638a0707379913
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285404"
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
