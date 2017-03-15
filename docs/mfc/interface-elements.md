---
title: "Elementos de la interfaz | Microsoft Docs"
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
  - "arquitectura [C++], MFC Feature Pack"
  - "MFC Feature Pack, arquitectura"
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# Elementos de la interfaz
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este documento describe los elementos de la interfaz que se introdujeron en [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] SP1, y también describe diferencias con la versión anterior de la biblioteca.  
  
 La ilustración siguiente se muestra una aplicación compilada con los nuevos elementos de la interfaz.  
  
 ![Aplicación de ejemplo de MFC Feature Pack](../mfc/media/mfc_featurepack.png "MFC\_FeaturePack")  
  
## Acoplamiento de la ventana  
 La funcionalidad de acoplamiento de la ventana se parece al acoplamiento de la ventana que la interfaz gráfica de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] utiliza.  
  
## Las barras de control son paneles de Menú  
 Las barras de control ahora se conocen como paneles y se derivan de [CBasePane Class](../mfc/reference/cbasepane-class.md).  En versiones anteriores de MFC, la clase base de las barras de control se `CControlBar`.  
  
 La ventana de marco principal de la aplicación se representa normalmente mediante [CFrameWndEx Class](../mfc/reference/cframewndex-class.md) o [CMDIFrameWndEx \(Clase\)](../mfc/reference/cmdiframewndex-class.md).  El cuadro principal se denomina *el sitio de vinculación*.  Los paneles pueden tener uno de los tres tipos de elementos principales: un sitio de vinculación, una barra de acoplamiento, o una ventana de mini\- cuadro.  
  
 Hay dos tipos de paneles: no puede cambiar y puede cambiar.  Los paneles de tamaño variable, como barras de estado y barras de herramientas, se puede cambiar el tamaño mediante los divisores o los controles deslizantes.  Los paneles de tamaño variable pueden formar contenedores \(un panel se puede acoplar a otro panel, creando un divisor entre ellos\).  Sin embargo, los paneles tamaño no se pueden adjuntar \(acopla\) para acoplar barras.  
  
 Si la aplicación utiliza los paneles no existe, derívelos de [CPane Class](../mfc/reference/cpane-class.md).  Si la aplicación utiliza los paneles de tamaño variable, derívelos de [CDockablePane Class](../mfc/reference/cdockablepane-class.md)  
  
## Acople el sitio  
 El sitio de vinculación \(o la ventana de marco principal\) posee todos los paneles y ventanas de mini\- cuadro en una aplicación.  El sitio de vinculación contiene un miembro de [CDockingManager](../mfc/reference/cdockingmanager-class.md) .  Este miembro mantiene una lista de todos los paneles que pertenecen al sitio de vinculación.  Se ordena la lista para colocar los paneles creados en los bordes externa del sitio de vinculación al principio de la lista.  Cuando el marco dibuja de nuevo el sitio dock, recorre sobre esta lista y ajusta el diseño de cada panel para incluir el rectángulo delimitador actual del sitio de vinculación.  Puede llamar a `AdjustDockingLayout` o `RecalcLayout` cuando tiene que ajustar el diseño de acoplamiento, y el marco redirige esta llamada al administrador de acoplamiento.  
  
## Barras de vinculación  
 Cada ventana de marco principal puede colocar *barras de vinculación* a lo largo de los bordes.  Una barra de vinculación es un panel que pertenece a [CDockSite Class](../mfc/reference/cdocksite-class.md).  Las barras de vinculación pueden aceptar los objetos derivados de [CPane](../mfc/reference/cpane-class.md), como barras de herramientas.  Para crear barras de vinculación cuando se inicializa la ventana de marco principal, llame a `EnableDocking`.  Para habilitar las barras automático de ocultar, llame a `EnableAutoHideBars`.  `EnableAutoHideBars` crea los objetos de [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) , y las posiciones al lado de cada barra de vinculación.  
  
 Cada barra de vinculación se divide en filas de vinculación.  Las filas de vinculación se representan mediante [CDockingPanesRow Class](../mfc/reference/cdockingpanesrow-class.md).  Cada fila de vinculación contiene una lista de barras de herramientas.  Si un usuario acopla una barra de herramientas o mueva la barra de herramientas a una fila a otra dentro de la misma barra de acoplamiento, el marco o crea una nueva fila y cambia el tamaño de la barra de vinculación en consecuencia, o la las posiciones la barra de herramientas respecto a una fila existente.  
  
## Mini\-cuadro Windows  
 Un panel flotante reside en una ventana de mini\- cuadro.  Las ventanas de Mini\- cuadro se representan mediante dos clases: [CMDITabInfo Class](../mfc/reference/cmditabinfo-class.md) \(que sólo pueden contener un panel\) y [CMultiPaneFrameWnd Class](../mfc/reference/cmultipaneframewnd-class.md) \(que pueden contener varios paneles\).  Para desacoplar un panel en el código, llame a [CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md).  Después de que un panel flota, el marco de trabajo crea automáticamente una ventana de mini\- cuadro y esa ventana de mini\- cuadro se convierte en el elemento primario flotante del panel.  Cuando se acopla de punto flotante de panel, el marco reinicializan su elemento primario, y el panel flotante se convierte en una barra de vinculación \(para las barras de herramientas\) o un sitio de vinculación \(para los paneles de tamaño variable\).  
  
## Divisores de paneles  
 Los divisores de paneles \(también denominados controles deslizantes o divisores\) se representan mediante [CPaneDivider Class](../mfc/reference/cpanedivider-class.md).  Cuando un usuario acoplar un panel, el marco de trabajo crea los divisores de paneles, independientemente de si el panel está acoplado en el sitio de vinculación o en otro panel.  Cuando se acopla de un panel al sitio de acoplamiento, el divisor de paneles se denominan *el divisor de paneles predeterminado*.  El divisor de paneles predeterminado es responsable del diseño de todos los paneles de acoplamiento en el sitio de vinculación.  El administrador de vinculación mantiene una lista de divisores de paneles predeterminados, y una lista de paneles.  Los administradores de vinculación son responsables de diseño de todos los paneles de acoplamiento.  
  
## Contenedores  
 Todos los paneles de tamaño variable, cuando se acoplan entre sí, se mantienen en contenedores.  Los contenedores son representados por [CPaneContainer Class](../mfc/reference/cpanecontainer-class.md).  Cada contenedor tiene punteros al panel izquierdo, el panel derecho, el sub\- contenedor izquierdo, el sub\- contenedor derecho, y el divisor entre las partes izquierda y derecha. \(*Los Left y right* no hacen referencia a lados físicos pero identifican bastante bifurcaciones de una estructura de árbol\). De esta manera se puede compilar un árbol de paneles y de divisores y por consiguiente para lograr diseños complejos de paneles que se ajusten su tamaño juntos.  La clase de `CPaneContainer` mantiene el árbol de contenedores; ella también mantiene dos listas de paneles y controles deslizantes que residen en este árbol.  Incrustar los administradores del contenedor del panel normalmente en los controles deslizantes predeterminados y las ventanas de mini\- cuadro que contienen varios paneles.  
  
## Ocultar automáticamente las barras de control  
 De forma predeterminada, cada `CDockablePane` admite la característica de ocultar automáticamente.  Cuando un usuario hace clic en el botón de alfiler en la leyenda de `CDockablePane`, el marco cambia el panel a ocultar automáticamente el modo.  Para controlar el clic, el marco de trabajo crea [CMFCAutoHideBar Class](../mfc/reference/cmfcautohidebar-class.md) y [CMFCAutoHideButton Class](../mfc/reference/cmfcautohidebutton-class.md) asociados al objeto de `CMFCAutoHideBar` .  El marco coloca nuevo `CMFCAutoHideBar` en [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md).  El marco de trabajo también asocia `CMFCAutoHideButton` a la barra de herramientas.  [CDockingManager Class](../mfc/reference/cdockingmanager-class.md) mantiene `CDockablePane`.  
  
## Barras de controles y barras de Outlook con pestañas  
 [CMFCBaseTabCtrl Class](../mfc/reference/cmfcbasetabctrl-class.md) implementa la funcionalidad básica de una ventana con fichas con pestañas desmontables.  Para utilizar un objeto de `CMFCBaseTabCtrl` , inicialice [CBaseTabbedPane \(Clase\)](../mfc/reference/cbasetabbedpane-class.md) en la aplicación.  `CBaseTabbedPane` se deriva de `CDockablePane` y mantiene un puntero a un objeto de `CMFCBaseTabCtrl` .  `CBaseTabbedPane` permite a los usuarios para acoplar y para cambiar el tamaño de las barras de controles con fichas.  Uso [CDockablePane::AttachToTabWnd](../Topic/CDockablePane::AttachToTabWnd.md) de crear dinámicamente las barras de control que se acoplan y con fichas.  
  
 El control de barra de Outlook también se basa en las barras con fichas.  [CMFCOutlookBar \(Clase\)](../mfc/reference/cmfcoutlookbar-class.md) se deriva de `CBaseTabbedPane`.  Para obtener más información sobre cómo utilizar la barra de Outlook, vea [CMFCOutlookBar \(Clase\)](../mfc/reference/cmfcoutlookbar-class.md).  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)