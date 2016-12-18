---
title: "Configurar las im&#225;genes para un elemento individual | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "imágenes [C++], elementos de cuadro combinado"
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configurar las im&#225;genes para un elemento individual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los valores de `iImage`, **iSelectedImage**, y los miembros de **iOverlay** de la estructura de [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) determinan los distintos tipos de imágenes utilizadas por el elemento extendido de cuadro combinado.  Cada valor es el índice de una imagen en la lista asociada del control.  De forma predeterminada, establecen a estos miembros a 0, lo que hace que el control no muestra ninguna imagen para el elemento.  Si desea utilizar imágenes para un elemento específico, puede modificar la estructura en consecuencia, ya sea al insertar el elemento del cuadro combinado o modifica un elemento existente del cuadro combinado.  
  
## Establecer la Imagen para un nuevo elemento  
 Si está insertando un nuevo elemento, inicialice `iImage`, **iSelectedImage**, y los miembros de la estructura de **iOverlay** con los valores adecuados y después incrustan el elemento con una llamada a [CComboBoxEx::InsertItem](../Topic/CComboBoxEx::InsertItem.md).  
  
 El ejemplo siguiente inserta un nuevo elemento extendido de cuadro combinado \(`cbi`\) en el control extendido de cuadro combinado \(`m_comboEx`\), proporcionando índices para las tres estados de imagen:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/CPP/setting-the-images-for-an-individual-item_1.cpp)]  
  
## Establecer la Imagen para un elemento existente  
 Si está modificando un elemento existente, debe ejecutar el miembro de **MASK** de una estructura de **COMBOBOXEXITEM** .  
  
#### Para modificar un elemento existente para utilizar imágenes  
  
1.  Declare una estructura de **COMBOBOXEXITEM** y el miembro de datos de **MASK** a valores que está interesado en modificaciones.  
  
2.  Mediante esta estructura, haga una llamada a [CComboBoxEx::GetItem](../Topic/CComboBoxEx::GetItem.md).  
  
3.  Modifique **MASK**, `iImage`, y los miembros de **iSelectedImage** de estructura recién devuelta, utilizando los valores adecuados.  
  
4.  Haga una llamada a [CComboBoxEx::SetItem](../Topic/CComboBoxEx::SetItem.md), pasando la estructura modificada.  
  
 El ejemplo siguiente se muestra este procedimiento cambiando las imágenes seleccionadas y no seleccionadas del tercer elemento extendido de cuadro combinado:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/CPP/setting-the-images-for-an-individual-item_2.cpp)]  
  
## Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)