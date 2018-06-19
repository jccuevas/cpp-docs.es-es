---
title: Configurar las imágenes para un elemento Individual | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7f3dbdf4d386e40802d74459dd2854035b5b7c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380606"
---
# <a name="setting-the-images-for-an-individual-item"></a>Configurar las imágenes para un elemento individual
Los distintos tipos de imágenes usadas por el elemento de cuadro combinado extendido se determinan por los valores de la `iImage`, **iSelectedImage**, y **iOverlay** los miembros de la [COMBOBOXEXITEM ](http://msdn.microsoft.com/library/windows/desktop/bb775746) estructura. Cada valor es el índice de una imagen en la lista de imágenes asociadas del control. De forma predeterminada, estos miembros se establecen en 0, haciendo que el control no mostrará ninguna imagen para el elemento. Si desea utilizar imágenes para un elemento específico, puede modificar la estructura en consecuencia, cuando se inserta el elemento de cuadro combinado o mediante la modificación de un elemento de cuadro combinado existente.  
  
## <a name="setting-the-image-for-a-new-item"></a>Establecer la imagen de un nuevo elemento  
 Si va a insertar un nuevo elemento, inicialice la `iImage`, **iSelectedImage**, y **iOverlay** miembros con los valores adecuados de estructura y, a continuación, inserte el elemento con una llamada a [ CComboBoxEx:: InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).  
  
 En el ejemplo siguiente se inserta un nuevo elemento de cuadro combinado extendido (`cbi`) en el control de cuadro combinado extendido (`m_comboEx`), proporcionando índices para los tres estados de imagen:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>Establecer la imagen de un elemento existente  
 Si va a modificar un elemento existente, debe trabajar con el **máscara** miembro de un **COMBOBOXEXITEM** estructura.  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>Para modificar un elemento existente para usar imágenes  
  
1.  Declarar un **COMBOBOXEXITEM** estructurar y establecer el **máscara** los valores de miembro de datos está interesado en modificar.  
  
2.  Con esta estructura, realizar una llamada a [CComboBoxEx:: GetItem](../mfc/reference/ccomboboxex-class.md#getitem).  
  
3.  Modificar el **máscara**, `iImage`, y **iSelectedImage** miembros de la estructura recién devuelta, usando los valores adecuados.  
  
4.  Realizar una llamada a [CComboBoxEx:: SetItem](../mfc/reference/ccomboboxex-class.md#setitem), pasando la estructura modificada.  
  
 En el ejemplo siguiente se muestra este procedimiento intercambiando las imágenes seleccionadas y del tercer elemento de cuadro combinado extendido:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)

