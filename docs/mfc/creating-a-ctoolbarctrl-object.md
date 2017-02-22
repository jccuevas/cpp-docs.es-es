---
title: "Crear un objeto CToolBarCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CToolBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl (clase), crear barras de herramientas"
  - "controles de barra de herramientas [MFC], crear"
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Crear un objeto CToolBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

los objetos de[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) contienen varias estructuras de datos internas \(una lista de mapas de bits del botón, una lista de cadenas de la etiqueta del botón, y una lista de estructuras de `TBBUTTON` — ese asociar una imagen o una cadena con la posición, el estilo, estado, y el identificador de comando del botón.  Cada uno de los elementos de estas estructuras de datos se está haciendo referencia por un índice cero\- basado.  Antes de poder utilizar un objeto de `CToolBarCtrl` , debe configurar estas estructuras de datos.  Para obtener una lista de estructuras de datos, vea [Controles toolbar](https://msdn.microsoft.com/en-us/library/47xcww9x.aspx) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  La lista de cadenas sólo se puede utilizar para las etiquetas del botón; no se puede recuperar cadenas de la barra de herramientas.  
  
 Para utilizar un objeto de `CToolBarCtrl` , realizará normalmente estos pasos:  
  
### Para utilizar un objeto de CToolBarCtrl  
  
1.  Cree el objeto de [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .  
  
2.  Llame a [crear](../Topic/CToolBarCtrl::Create.md) para crear el control común de la barra de herramientas de Windows y para adjuntarlo al objeto de `CToolBarCtrl` .  Si desea que las imágenes de mapa de bits en los botones, agregue los mapas de bits del botón en la barra de herramientas llamando a [AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md).  Si desea que las etiquetas de la cadena en los botones, agregue las cadenas a la barra de herramientas llamando a [AddString](../Topic/CToolBarCtrl::AddString.md) y\/o [AddStrings](../Topic/CToolBarCtrl::AddStrings.md).  Después de llamar a `AddString` y\/o `AddStrings`, debe llamar a [Ajustar automáticamente](../Topic/CToolBarCtrl::AutoSize.md) para obtener la cadena o cadenas que aparezca.  
  
3.  Agregue las estructuras del botón en la barra de herramientas llamando a [AddButtons](../Topic/CToolBarCtrl::AddButtons.md).  
  
4.  Si desea información sobre herramientas, los mensajes de **TTN\_NEEDTEXT** ID en la ventana propietaria de la barra de herramientas como se describe en [Administrar notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md).  
  
5.  Si desea que el usuario pueda personalizar la barra de herramientas, los mensajes de notificación de personalización de identificador en la ventana propietaria como se describe en [Administrar notificaciones de personalización](../mfc/handling-customization-notifications.md).  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)