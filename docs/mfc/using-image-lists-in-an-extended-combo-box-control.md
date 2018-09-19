---
title: Usar listas de imágenes en un Control de cuadro combinado extendido | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a701871631fead48c22b1ffb2cbc3c386b960
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383350"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Usar listas de imágenes en un control de cuadro combinado extendido
La característica principal de los controles de cuadro combinado extendido es la capacidad para asociar imágenes de una lista de imágenes con elementos individuales de un control de cuadro combinado. Cada elemento es capaz de mostrar tres imágenes distintas: una para su estado seleccionado, uno para su estado no y una tercera para una imagen de superposición.  
  
 El procedimiento siguiente asocia una lista de imágenes con un control de cuadro combinado extendido:  
  
### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Para asociar una lista de imágenes con un control de cuadro combinado extendido  
  
1.  Crear una nueva lista de imágenes (o utilice un objeto de lista de imágenes existente), utilizando la [CImageList](../mfc/reference/cimagelist-class.md) constructor y almacenando el puntero resultante.  
  
2.  Inicializar el nuevo objeto de lista de imagen mediante una llamada a [CImageList:: Create](../mfc/reference/cimagelist-class.md#create). El código siguiente es un ejemplo de esta llamada.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  Agregue imágenes opcionales para cada estado posible: seleccionado o no seleccionado y uno superpuesto. El código siguiente agrega tres imágenes predefinidas.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  Asociar la lista de imágenes con el control con una llamada a [CComboBoxEx:: SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).  
  
 Una vez que se ha asociado con el control de la lista de imágenes, puede especificar individualmente las imágenes de que cada elemento va a usar para los tres estados posibles. Para obtener más información, consulte [configurar las imágenes para un elemento Individual](../mfc/setting-the-images-for-an-individual-item.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)

