---
title: "Usar un control de animaci&#243;n | Microsoft Docs"
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
  - "controles de animación [C++]"
  - "CAnimateCtrl (clase), controles de animación"
  - "controles [MFC], animación"
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar un control de animaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso típico de una animación sigue el modelo siguiente:  
  
-   Se crea el control.  Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. \(Debe tener un miembro de [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) en la clase de diálogo correspondiente al control de animación\). Alternativamente, puede utilizar la función miembro de [crear](../Topic/CAnimateCtrl::Create.md) para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Cargue AVI clip en el control de la aplicación llamando a la función miembro de [Abierta](../Topic/CAnimateCtrl::Open.md) .  Si el control de animación está en un cuadro de diálogo, un buen lugar para ello es la función de [OnInitDialog](../Topic/CDialog::OnInitDialog.md) de la clase de diálogo.  
  
-   Reproducir recorte llamando a la función miembro de [Reproducir](../Topic/CAnimateCtrl::Play.md) .  Si el control de animación está en un cuadro de diálogo, un buen lugar para ello es la función de **OnInitDialog** de la clase de diálogo.  La llamada **Reproducir** no es necesaria si el control de animación tiene el estilo de `ACS_AUTOPLAY` establecido.  
  
-   Si desea mostrar partes de recorte o para jugarlas cuadro por el cuadro, utilice la función miembro de `Seek` .  Para detener recorte que se está reproduciendo, utilice la función miembro de `Stop` .  
  
-   Si no va a destruir el control inmediatamente, quite clip de memoria llamando a la función miembro de **cerrar** .  
  
-   Si el control de animación está en un cuadro de diálogo, éste y el objeto de `CAnimateCtrl` se destruyeron automáticamente.  Si no, deberá asegurarse de que el control y el objeto de `CAnimateCtrl` están destruirse correctamente.  La destrucción del control automáticamente cierra AVI recorte.  
  
## Vea también  
 [Usar CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Controles](../mfc/controls-mfc.md)