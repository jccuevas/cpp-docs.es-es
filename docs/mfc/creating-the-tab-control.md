---
title: "Crear el control de pesta&#241;a | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TCS_EX_REGISTERDROP"
  - "TCS_EX_FLATSEPARATORS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabCtrl (clase), crear"
  - "controles de fichas, crear"
  - "TCS_EX_FLATSEPARATORS (estilo extendido)"
  - "TCS_EX_REGISTERDROP (estilo extendido)"
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Crear el control de pesta&#241;a
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cómo se crea el control de ficha depende de si utiliza el control en un cuadro de diálogo o se está realizando en una ventana de nondialog.  
  
### Para utilizar CTabCtrl directamente en un cuadro de diálogo  
  
1.  En el editor de cuadros de diálogo, agregue un Control tab el recurso de plantilla de cuadro de diálogo.  Especifique el identificador de control  
  
2.  Utilice [Asistente para agregar variables miembro](../ide/adding-a-member-variable-visual-cpp.md) para agregar una variable miembro de [CTabCtrl](../mfc/reference/ctabctrl-class.md) escrito con la propiedad del Control.  Puede utilizar este miembro para llamar a funciones miembro de `CTabCtrl` .  
  
3.  Funciones de controlador de mapa en la clase de diálogo para los mensajes de notificación del control de ficha que necesite controlar.  Para obtener más información, vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md).  
  
4.  En [OnInitDialog](../Topic/CDialog::OnInitDialog.md), establezca los estilos para `CTabCtrl`.  
  
### Para utilizar CTabCtrl en una ventana de nondialog  
  
1.  Defina el control en la vista o la clase de ventana.  
  
2.  Llame a la función miembro de [crear](../Topic/CTabCtrl::Create.md) de control, posiblemente en [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md), posiblemente ya desde la función controladora de [OnCreate](../Topic/CWnd::OnCreate.md) de la ventana primaria \(si está creando subclases el control\).  Establezca los estilos del control.  
  
 Después de crear el objeto de `CTabCtrl` , puede establecer o borrar los estilos extendidos siguientes:  
  
-   El control de ficha de**TCS\_EX\_FLATSEPARATORS**The dibujará los separadores entre los elementos de pestaña.  Este estilo extendido solo afecta a los controles de ficha que tienen los estilos de **TCS\_BUTTONS** y de **TCS\_FLATBUTTONS** .  De forma predeterminada, crear el control de ficha con el estilo de **TCS\_FLATBUTTONS** establece este estilo extendido.  
  
-   El control de ficha de**TCS\_EX\_REGISTERDROP**The genera los mensajes de notificación de **TCN\_GETOBJECT** para solicitar un objeto de destino cuando se arrastra un objeto sobre los elementos de la pestaña en el control.  
  
    > [!NOTE]
    >  Para recibir notificación de **TCN\_GETOBJECT** , debe inicializar las bibliotecas VIEJAS con una llamada a [AfxOleInit](../Topic/AfxOleInit.md).  
  
 Estos estilos se pueden recuperar y establecer, después de haber creado el control, con llamadas respectivas a las funciones miembro de [GetExtendedStyle](../Topic/CTabCtrl::GetExtendedStyle.md) y de [SetExtendedStyle](../Topic/CTabCtrl::SetExtendedStyle.md) .  
  
 Por ejemplo, establezca el estilo de **TCS\_EX\_FLATSEPARATORS** con las siguientes líneas de código:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/CPP/creating-the-tab-control_1.cpp)]  
  
 Desactive el estilo de **TCS\_EX\_FLATSEPARATORS** de un objeto de `CTabCtrl` con las siguientes líneas de código:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/CPP/creating-the-tab-control_2.cpp)]  
  
 Esto quitará los separadores que aparecen entre los botones del objeto de `CTabCtrl` .  
  
## Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)