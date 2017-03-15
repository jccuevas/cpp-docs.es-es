---
title: "Usar un control de tecla de acceso r&#225;pido | Microsoft Docs"
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
  - "CHotKeyCtrl (clase), utilizar"
  - "controles de tecla de acceso rápido"
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar un control de tecla de acceso r&#225;pido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso típico de una tecla de acceso rápido sigue el modelo siguiente:  
  
-   Se crea el control.  Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. \(Debe tener un miembro de [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) en la clase de diálogo correspondiente al control de la tecla de acceso rápido\). Alternativamente, puede utilizar la función miembro de [crear](../Topic/CHotKeyCtrl::Create.md) para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Si desea establecer un valor predeterminado para el control, llame a la función miembro de [SetHotKey](../Topic/CHotKeyCtrl::SetHotKey.md) .  Si desea prohibir a ciertos estados de cambio, llame a [SetRules](../Topic/CHotKeyCtrl::SetRules.md).  Para los controles de un cuadro de diálogo, un buen momento para ello es la función de [OnInitDialog](../Topic/CDialog::OnInitDialog.md) del cuadro de diálogo.  
  
-   El usuario interactúa con el control presionando una combinación de teclas de acceso rápido al control de la tecla de acceso rápido tiene el foco.  El usuario a indica de algún modo que esta tarea se completa, quizás haciendo clic en un botón del cuadro de diálogo.  
  
-   Cuando se notifica al programa que el usuario ha seleccionado una tecla de acceso rápido, debe utilizar la función [GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md) miembro para recuperar los valores virtuales de estado de clave y de cambio de control de la tecla de acceso rápido.  
  
-   Una vez que ya sabe qué clave puede establecer el usuario seleccionado, la tecla de acceso rápido utilizando uno de los métodos descritos en [Establecer una tecla de acceso rápido](../mfc/setting-a-hot-key.md).  
  
-   Si el control de la tecla de acceso rápido está en un cuadro de diálogo, éste y el objeto de `CHotKeyCtrl` se destruyeron automáticamente.  Si no, deberá asegurarse de que el control y el objeto de `CHotKeyCtrl` están destruirse correctamente.  
  
## Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)