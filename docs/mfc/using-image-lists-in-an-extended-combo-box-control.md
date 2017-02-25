---
title: "Usar listas de im&#225;genes en un control de cuadro combinado extendido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cuadros combinados extendidos, imágenes"
  - "listas de imágenes [C++], cuadros combinados"
  - "imágenes [C++], elementos de cuadro combinado"
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Usar listas de im&#225;genes en un control de cuadro combinado extendido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La característica principal de los controles extendidos de cuadro combinado es la capacidad de asociar imágenes de una imagen con elementos individuales en un control de cuadro combinado.  Cada elemento puede mostrar tres imágenes diferentes: uno para el estado seleccionado, uno para el estado nonselected, y una tercera para una imagen de superposición.  
  
 El procedimiento siguiente asocia una lista de imágenes a un control extendido de cuadro combinado:  
  
### Para asociar una lista de imágenes con un control extendido de cuadro combinado  
  
1.  Construye una nueva lista de imágenes \(o use un objeto existente de la lista de imágenes\), utilizando el constructor de [CImageList](../mfc/reference/cimagelist-class.md) y almacenar el puntero resultante.  
  
2.  Inicializa el nuevo objeto de la lista de imágenes llamando a [CImageList::Create](../Topic/CImageList::Create.md).  El código siguiente es un ejemplo de esta llamada.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/CPP/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  Agregue imágenes opcionales para cada posible estado: seleccionado o nonselected, y una superposición.  El código siguiente agrega tres imágenes predefinidas.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/CPP/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  Asociar la lista de imágenes con el control con una llamada a [CComboBoxEx::SetImageList](../Topic/CComboBoxEx::SetImageList.md).  
  
 Una vez que la lista de imágenes se ha asociado al control, puede especificar individualmente las imágenes que cada elemento utilizará para los tres estados posibles.  Para obtener más información, vea [Establecer las Imágenes para un elemento individual](../mfc/setting-the-images-for-an-individual-item.md).  
  
## Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)