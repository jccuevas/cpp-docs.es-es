---
title: "Crear un control Rebar | Microsoft Docs"
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
  - "CReBarCtrl (clase), crear"
  - "controles rebar, crear"
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Crear un control Rebar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

los objetos de[CReBarCtrl](../mfc/reference/crebarctrl-class.md) deben crearse antes de que el objeto primario esté visible.  Esto reduce las posibilidades de los problemas de representación.  
  
 Por ejemplo, los controles rebar \(utilizados en objetos de la ventana de marco\) se utilizan como ventanas principales para los controles de barra de herramientas.  Por consiguiente, el elemento primario del control rebar es el objeto de la ventana de marco.  Dado que el objeto de la ventana de marco es el elemento primario, la función miembro de `OnCreate` \(primario\) es un lugar excelente para crear el control rebar.  
  
 Para utilizar un objeto de `CReBarCtrl` , realizará normalmente estos pasos:  
  
### Para utilizar un objeto de CReBarCtrl  
  
1.  Cree el objeto de [CReBarCtrl](../mfc/reference/crebarctrl-class.md) .  
  
2.  Llame a [crear](../Topic/CReBarCtrl::Create.md) para crear el control común del rebar de Windows y para adjuntarlo al objeto de `CReBarCtrl` , especificando cualquier estilo deseado.  
  
3.  Cargue un mapa de bits, con una llamada a [CBitmap::LoadBitmap](../Topic/CBitmap::LoadBitmap.md), para utilizarse como el fondo del objeto de control rebar.  
  
4.  Cree e inicialice cualquier objeto de ventana secundaria \(barras de herramientas, controles de cuadro de diálogo, etc.\) incluido en el objeto de control rebar.  
  
5.  Inicializa una estructura de **REBARBANDINFO** con la información necesaria para la banda alrededor que se va a insertar.  
  
6.  Llame a [InsertBand](../Topic/CReBarCtrl::InsertBand.md) para insertar las ventanas secundarias existentes \(como `m_wndReToolBar`\) en el nuevo control rebar.  Para obtener más información sobre cómo insertar bandas en un control existente rebar, vea [Controles y Bandas Rebar](../mfc/rebar-controls-and-bands.md).  
  
## Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)