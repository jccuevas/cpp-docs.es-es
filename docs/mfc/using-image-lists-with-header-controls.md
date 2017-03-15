---
title: "Usar listas de im&#225;genes con controles de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), listas de imágenes"
  - "controles del encabezado, listas de imágenes"
  - "listas de imágenes [C++], controles del encabezado"
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar listas de im&#225;genes con controles de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los elementos de encabezado tienen la capacidad de mostrar una imagen dentro de un elemento de encabezado.  Esta imagen, almacenada en una lista asociada de la imagen, es 16 x 16 píxeles y tiene las mismas características que las imágenes de icono utilizada en un control de vista de lista.  Para implementar este comportamiento correctamente, debe crear e inicializar la lista de imágenes, asociar la lista con el control de encabezado, y modifique los atributos del elemento de encabezado que mostrará la imagen.  
  
 El procedimiento siguiente muestra los detalles, mediante un puntero a un control de encabezado \(`m_pHdrCtrl`\) y un puntero a una lista de imágenes \(`m_pHdrImages`\).  
  
### Para mostrar una imagen en un elemento de encabezado  
  
1.  Construye una nueva imagen lista \(o utilice un objeto existente de la lista de imágenes\) mediante el constructor de [CImageList](../mfc/reference/cimagelist-class.md) , almacenando el puntero resultante.  
  
2.  Inicializa el nuevo objeto de la lista de imágenes llamando a [CImageList::Create](../Topic/CImageList::Create.md).  El código siguiente es un ejemplo de esta llamada.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_1.cpp)]  
  
3.  Agregue imágenes para cada elemento de encabezado.  El código siguiente agrega dos imágenes predefinidas.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_2.cpp)]  
  
4.  Asociar la lista de imágenes con el control de encabezado con una llamada a [CHeaderCtrl::SetImageList](../Topic/CHeaderCtrl::SetImageList.md).  
  
5.  Modifique el elemento de encabezado para mostrar una imagen de la lista asociada de la imagen.  El ejemplo siguiente se asigna la primera imagen, de `m_phdrImages`, al primer elemento de encabezado, `m_pHdrCtrl`.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/CPP/using-image-lists-with-header-controls_3.cpp)]  
  
 Para obtener información detallada sobre los valores de parámetros utilizados, vea [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)pertinente.  
  
> [!NOTE]
>  Es posible tener varios controles utilizando la misma lista de imágenes.  Por ejemplo, en un control estándar de la vista de lista, puede haber una lista de imágenes \(16 x 16 imágenes de píxeles\) utilizada por tanto la pequeña vista de iconos de un control de vista de lista y los elementos de encabezado de la vista de lista controlan.  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)