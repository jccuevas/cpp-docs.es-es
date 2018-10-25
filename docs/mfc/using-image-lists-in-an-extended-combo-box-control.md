---
title: Usar listas de imágenes en un Control de cuadro combinado extendido | Microsoft Docs
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
ms.openlocfilehash: 15b069c1075a1b2b7db484da588684fca280ef29
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083404"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Usar listas de imágenes en un control de cuadro combinado extendido

La característica principal de los controles de cuadro combinado extendido es la capacidad de asociar las imágenes de una lista de imágenes con elementos individuales de un control de cuadro combinado. Cada elemento es capaz de mostrar tres imágenes diferentes: uno para su estado seleccionado, uno para su estado no y un tercero para una imagen de superposición.

El procedimiento siguiente asocia una lista de imágenes a un control de cuadro combinado extendido:

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Para asociar una lista de imágenes a un control de cuadro combinado extendido

1. Construir una lista de imágenes (o utilice un objeto de lista de imágenes existente), mediante el [CImageList](../mfc/reference/cimagelist-class.md) constructor y almacenando el puntero resultante.

1. Inicializar el nuevo objeto de lista de imágenes mediante una llamada a [CImageList:: Create](../mfc/reference/cimagelist-class.md#create). El código siguiente es un ejemplo de esta llamada.

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. Agregar imágenes opcionales para cada estado posible: seleccionado o no seleccionado y una superposición. El código siguiente agrega tres imágenes predefinidas.

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. Asociar la lista de imágenes con el control con una llamada a [CComboBoxEx:: SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).

Una vez que se ha asociado con el control de la lista de imágenes, puede especificar individualmente las imágenes de que cada elemento va a utilizar para los tres estados posibles. Para obtener más información, consulte [configurar las imágenes para un elemento Individual](../mfc/setting-the-images-for-an-individual-item.md).

## <a name="see-also"></a>Vea también

[Uso de CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)

