---
title: Configurar las imágenes para un elemento individual
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
ms.openlocfilehash: 177c06acfe665a43921b19407d9d357d4545e748
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511274"
---
# <a name="setting-the-images-for-an-individual-item"></a>Configurar las imágenes para un elemento individual

Los distintos tipos de imágenes utilizados por el elemento del cuadro combinado extendido vienen determinados por los valores de los miembros *iImage*, *iSelectedImage*y *IOverlay* de la estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) . Cada valor es el índice de una imagen en la lista de imágenes asociada del control. De forma predeterminada, estos miembros se establecen en 0, lo que hace que el control no muestre ninguna imagen para el elemento. Si desea usar imágenes para un elemento específico, puede modificar la estructura en consecuencia, bien al insertar el elemento de cuadro combinado o al modificar un elemento de cuadro combinado existente.

## <a name="setting-the-image-for-a-new-item"></a>Establecimiento de la imagen de un nuevo elemento

Si va a insertar un nuevo elemento, inicialice los miembros de la estructura *iImage*, *iSelectedImage*y *IOverlay* con los valores adecuados y, a continuación, inserte el elemento con una llamada a [CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).

En el ejemplo siguiente se inserta un nuevo elemento de cuadro combinado`cbi`extendido () en el control de cuadro`m_comboEx`combinado extendido (), proporcionando índices para los tres Estados de imagen:

[!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]

## <a name="setting-the-image-for-an-existing-item"></a>Establecimiento de la imagen de un elemento existente

Si va a modificar un elemento existente, debe trabajar con el miembro de *máscara* de una estructura **COMBOBOXEXITEM** .

#### <a name="to-modify-an-existing-item-to-use-images"></a>Para modificar un elemento existente para utilizar imágenes

1. Declare una estructura **COMBOBOXEXITEM** y establezca el miembro de datos *Mask* en los valores que le interesa modificar.

1. Con esta estructura, realice una llamada a [CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem).

1. Modifique los miembros *Mask*, *iImage*y *iSelectedImage* de la estructura que se acaba de devolver, con los valores adecuados.

1. Realice una llamada a [CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem)y pase la estructura modificada.

En el ejemplo siguiente se muestra este procedimiento mediante el intercambio de las imágenes seleccionadas y no seleccionadas del tercer elemento del cuadro combinado extendido:

[!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)
