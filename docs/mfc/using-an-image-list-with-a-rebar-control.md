---
title: "Usar una lista de imágenes con un Control Rebar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: acb4ed52982f7ab23dac044eeacf315f45aa1232
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Usar una lista de imágenes con un control Rebar
Cada banda rebar puede contener, entre otras cosas, una imagen de una lista de imágenes asociada. El procedimiento siguiente detallan los pasos necesarios para mostrar una imagen en una banda rebar.  
  
### <a name="to-display-images-in-a-rebar-band"></a>Para mostrar imágenes en una banda rebar  
  
1.  Asociar una lista de imágenes a su objeto de control rebar realizando una llamada a [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), pasando un puntero a una lista de imágenes existente.  
  
2.  Modificar el **REBARBANDINFO** estructura para asignar una imagen a una banda rebar:  
  
    -   Establecer el **fMask** miembro **RBBIM_IMAGE**, mediante el operador OR bit a bit para incluir indicadores adicionales según sea necesario.  
  
    -   Establecer el `iImage` miembro para el índice de la lista de imágenes de la imagen que se mostrará.  
  
3.  Inicializar a los miembros de datos restantes, como el tamaño, el texto y el identificador de la ventana secundaria contenida, con la información necesaria.  
  
4.  Inserte la nueva banda (con la imagen) con una llamada a [CReBarCtrl:: InsertBand](../mfc/reference/crebarctrl-class.md#insertband), pasando el **REBARBANDINFO** estructura.  
  
 En el siguiente ejemplo se supone que un objeto de lista de imágenes existente con dos imágenes se adjunta al objeto de control rebar (`m_wndReBar`). Una nueva banda rebar (definida por `rbi`), que contiene la primera imagen, se agrega con una llamada a `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

