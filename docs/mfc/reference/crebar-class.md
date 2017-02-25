---
title: "CReBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CReBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBar class"
  - "Internet Explorer 4.0 common controls"
  - "rebar controls, control bar"
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CReBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una barra de control que proporciona el diseño, la persistencia, y la información de estado del rebar controla.  
  
## Sintaxis  
  
```  
  
class CReBar : public CControlBar  
  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReBar::AddBar](../Topic/CReBar::AddBar.md)|Agrega una banda un rebar.|  
|[CReBar::Create](../Topic/CReBar::Create.md)|Crea el control rebar y lo asocia al objeto de `CReBar` .|  
|[CReBar::GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md)|Permite el acceso directo al control común subyacente.|  
  
## Comentarios  
 Un objeto rebar puede contener una variedad de ventanas secundarias, normalmente otros controles, incluidos cuadros de edición, barras de herramientas, y los cuadros de lista.  Un objeto rebar puede mostrar sus ventanas secundarias sobre un mapa de bits especificado.  La aplicación puede cambiar automáticamente el tamaño del rebar, o el usuario puede cambiar manualmente el tamaño del rebar haciendo clic o arrastrando su barra de.  
  
 ![Ejemplo de RebarMenu](../../mfc/reference/media/vc4sc61.png "vc4SC61")  
  
## Control Rebar  
 Un objeto rebar se comporta de forma similar a un objeto de la barra de herramientas.  Un rebar utiliza el mecanismo de la clic\-y\-fricción para cambiar el tamaño de sus bandas.  Un control rebar puede contener una o más bandas, con cada banda tiene cualquier combinación de una barra de agarrador, un mapa de bits, de una etiqueta de texto, y una ventana secundaria.  sin embargo, las bandas no pueden contener más de una ventana secundaria.  
  
 **CReBar** utiliza la clase de [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) para proporcionar la implementación.  Puede tener acceso al control rebar con [GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md) aprovechar las opciones de personalización del control.  Para obtener más información sobre los controles rebar, vea `CReBarCtrl`.  Para obtener más información sobre cómo utilizar los controles rebar, vea [Mediante CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
> [!CAUTION]
>  Los objetos del Rebar y control rebar no admiten el acoplamiento de barra de control MFC.  Si se llama **CRebar:: EnableDocking** , la aplicación validar.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo MFCIE de MFC](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)