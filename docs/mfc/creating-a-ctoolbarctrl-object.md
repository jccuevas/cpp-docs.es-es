---
title: Crear un objeto CToolBarCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CToolBarCtrl
dev_langs: C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e86fad8191c4dea2eed3ae34ec96ed853ac1deae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-ctoolbarctrl-object"></a>Crear un objeto CToolBarCtrl
[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objetos contienen varias estructuras de datos internas: una lista de mapas de bits de imagen de botón, una lista de cadenas de etiqueta de botón y una lista de `TBBUTTON` estructuras: que asociar una imagen o de cadena con la posición, el estilo, el estado, y Identificador de comando del botón. Cada uno de los elementos de estas estructuras de datos se conoce por un índice de base cero. Para poder usar un `CToolBarCtrl` de objeto, debe configurar estas estructuras de datos. Para obtener una lista de las estructuras de datos, vea [controles de barra de herramientas](controls-mfc.md) en el SDK de Windows. La lista de cadenas sólo puede utilizarse para las etiquetas de botón; no se puede recuperar las cadenas de la barra de herramientas.  
  
 Para usar un `CToolBarCtrl` de objeto, normalmente se siguen estos pasos:  
  
### <a name="to-use-a-ctoolbarctrl-object"></a>Para utilizar un objeto CToolBarCtrl  
  
1.  Construir la [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objeto.  
  
2.  Llame a [crear](../mfc/reference/ctoolbarctrl-class.md#create) para crear el control común de barra de herramientas de Windows y adjuntarlo a la `CToolBarCtrl` objeto. Si desea imágenes de mapa de bits para botones, agregue los mapas de bits de botón a la barra de herramientas mediante una llamada a [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Si desea que las etiquetas de cadena para botones, agregue las cadenas a la barra de herramientas mediante una llamada a [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) o [a AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Después de llamar a `AddString` o `AddStrings`, debe llamar a [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) con el fin de obtener la cadena o cadenas que aparezcan.  
  
3.  Agregar estructuras de botón a la barra de herramientas mediante una llamada a [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).  
  
4.  Si desea información sobre herramientas, controle **TTN_NEEDTEXT** mensajes en la ventana propietaria de la barra de herramientas, como se describe en [controlar notificaciones de sugerencia de herramienta](../mfc/handling-tool-tip-notifications.md).  
  
5.  Si desea que el usuario pueda personalizar la barra de herramientas, controlar mensajes de notificación de personalización en la ventana propietaria tal y como se describe en [controlar notificaciones de personalización](../mfc/handling-customization-notifications.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

