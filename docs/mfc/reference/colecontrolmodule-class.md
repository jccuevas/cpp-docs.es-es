---
title: "COleControlModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleControlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControlModule class"
  - "control modules"
  - "MFC ActiveX controls, OLE control modules"
  - "OLE control modules"
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COleControlModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base que se deriva un objeto agente de controles activex.  
  
## Sintaxis  
  
```  
class COleControlModule : public CWinApp  
```  
  
## Comentarios  
 Esta clase proporciona funciones miembro para inicializar el módulo de control.  Cada agente de controles activex que utiliza las clases de windows presentation foundation Microsoft sólo puede contener un objeto derivado de `COleControlModule`.  Se construye este objeto cuando se construyen otros objetos globales de C\+\+.  declare el objeto derivado de `COleControlModule` en el nivel global.  
  
 Para obtener más información sobre cómo utilizar la clase de `COleControlModule` , vea la clase y el caso [Controles ActiveX](../../mfc/mfc-activex-controls.md)de [CWinApp](../../mfc/reference/cwinapp-class.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [ejemplo TESTHELP de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)