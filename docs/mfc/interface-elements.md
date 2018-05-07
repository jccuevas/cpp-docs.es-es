---
title: Elementos de la interfaz | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25f9de4ab5f7d12d240625e0fdf5f857563e8ce2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="interface-elements"></a>Elementos de la interfaz
Este documento describe los elementos de interfaz que se introdujeron en [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] SP1 y también se describe las diferencias con la versión anterior de la biblioteca.  
  
 En la siguiente ilustración muestra una aplicación que se generó con los nuevos elementos de interfaz.  
  
 ![Aplicación de ejemplo de MFC Feature Pack](../mfc/media/mfc_featurepack.png "mfc_featurepack")  
  
## <a name="window-docking"></a>Ventana de acoplamiento  
 Ventana de acoplamiento funcionalidad es similar a la ventana de acoplamiento que la [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] usa la interfaz gráfica de usuario.  
  
## <a name="control-bars-are-now-panes"></a>Barras de control son ahora paneles  
 Barras de control se conocen ahora como paneles y se derivan [CBasePane clase](../mfc/reference/cbasepane-class.md). En versiones anteriores de MFC, la clase base de barras de control era `CControlBar`.  
  
 La ventana de marco principal de la aplicación normalmente se representa mediante el [CFrameWndEx clase](../mfc/reference/cframewndex-class.md) o [CMDIFrameWndEx (clase)](../mfc/reference/cmdiframewndex-class.md). Se llama el marco principal la *acoplar sitio*. Paneles pueden tener uno de los tres tipos de elementos primarios: un sitio de vinculación, una barra de acoplamiento o una ventana de marco reducido.  
  
 Hay dos tipos de paneles: invariable y puede cambiar el tamaño. Pueden cambiar el tamaño de los paneles de tamaño variable, como barras de estado y las barras de herramientas, mediante el uso de separadores o controles deslizantes. Paneles de tamaño variable pueden formar contenedores (se puede acoplar un panel a otro panel, crear un divisor entre ellos). Sin embargo, puede cambiar el tamaño paneles no pueden adjuntarse (acoplada) para acoplar barras.  
  
 Si la aplicación utiliza paneles invariable, derivar desde [clase CPane](../mfc/reference/cpane-class.md).  Si la aplicación utiliza los paneles de tamaño variable, derivar desde [clase CDockablePane](../mfc/reference/cdockablepane-class.md)  
  
## <a name="dock-site"></a>Sitio de vinculación  
 El sitio de vinculación (o la ventana de marco principal) posee todos los paneles y ventanas de marco reducido en una aplicación. El sitio de vinculación contiene un [CDockingManager](../mfc/reference/cdockingmanager-class.md) miembro. Este miembro mantiene una lista de todos los paneles que pertenecen al sitio de vinculación. La lista está ordenada por lo que los paneles creados en los bordes exteriores de sitio de vinculación se colocan al principio de la lista. Cuando el marco de trabajo vuelve a dibujarse el sitio de vinculación, se repite a lo largo de esta lista y ajusta el diseño de cada panel para incluir el rectángulo delimitador actual del sitio de vinculación. Puede llamar a `AdjustDockingLayout` o `RecalcLayout` cuando se tenga que ajustar el diseño de acoplamiento y el marco de trabajo redirige esta llamada para el Administrador de acoplamiento.  
  
## <a name="dock-bars"></a>Barras de acoplamiento  
 Puede colocar cada ventana de marco principal *acoplar barras* a lo largo de los bordes. Una barra de acoplamiento es un panel que pertenece a un [clase CDockSite](../mfc/reference/cdocksite-class.md). Acoplar barras pueden aceptar los objetos derivados de [CPane](../mfc/reference/cpane-class.md), por ejemplo, las barras de herramientas. Para crear barras de acoplamiento cuando se inicialice la ventana de marco principal, llame a `EnableDocking`. Para habilitar las barras de ocultación automática, llame a `EnableAutoHideBars`. `EnableAutoHideBars` crea [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md) objetos y los coloca junto a cada barra de acoplamiento.  
  
 Cada barra de acoplamiento se divide en filas de acoplamiento. Acoplar filas se representan mediante la [CDockingPanesRow clase](../mfc/reference/cdockingpanesrow-class.md). Cada fila de acoplamiento contiene una lista de las barras de herramientas. Si un usuario acopla una barra de herramientas o mueve la barra de herramientas de una fila a otra dentro de la misma barra de acoplamiento, el marco de trabajo ya sea crea una nueva fila y cambia el tamaño de la barra de acoplamiento en consecuencia, o coloca la barra de herramientas en una fila existente.  
  
## <a name="mini-frame-windows"></a>Ventanas de marco reducido  
 Un panel flotante reside en una ventana de marco reducido. Ventanas de marco reducido están representadas por dos clases: [CMDITabInfo clase](../mfc/reference/cmditabinfo-class.md) (que puede contener un solo panel) y [CMultiPaneFrameWnd clase](../mfc/reference/cmultipaneframewnd-class.md) (que puede contener varios paneles). Para hacer flotar un panel en el código, llame a [CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane). Después se desplaza de un panel, el marco de trabajo crea automáticamente una ventana de marco reducido y esa ventana de marco reducido se convierte en principal del panel flotante. Cuando se acopla el panel flotante, el marco de trabajo restablece a su elemento primario y el panel flotante se convierte en una barra de acoplamiento (para las barras de herramientas) o un sitio de vinculación (para los paneles de tamaño variable).  
  
## <a name="pane-dividers"></a>Divisores de paneles  
 Divisores de paneles (también denominadas controles deslizantes o divisores) se representan mediante la [CPaneDivider clase](../mfc/reference/cpanedivider-class.md). Cuando un usuario acopla un panel, el marco de trabajo crea los divisores de los paneles, independientemente de si el panel está acoplado en el sitio de vinculación o en otro panel. Cuando se acopla un panel en el sitio de vinculación, el divisor del panel se denomina la *predeterminado panel divisor*. El divisor de paneles predeterminada es responsable del diseño de todos los paneles de acoplamiento en el sitio de vinculación. El Administrador de acoplamiento mantiene una lista de los divisores de los paneles de forma predeterminada y una lista de paneles. Acoplar administradores son responsables de la disposición de todos los paneles de acoplamiento.  
  
## <a name="containers"></a>Contenedores  
 Todos los paneles de tamaño variable, cuando se acopla entre sí, se mantienen en contenedores. Los contenedores se representan mediante la [CPaneContainer clase](../mfc/reference/cpanecontainer-class.md). Cada contenedor tiene punteros en el panel izquierdo, panel derecho, subcontenedor izquierdo, derecho subcontenedor y el separador entre las partes izquierdas y derecha. (*Izquierda* y *derecho* no hacen referencia a los lados físicos, pero en su lugar identificar las ramas de una estructura de árbol.) De esta manera podemos crear un árbol de paneles y los separadores y, por tanto, lograr diseños complejos de paneles que pueden cambiarse entre sí. La `CPaneContainer` clase mantiene el árbol de contenedores; también mantiene dos listas de paneles y los controles deslizantes que residen en este árbol. Administradores de contenedor de panel normalmente se incrustan en los controles deslizantes de forma predeterminada y ventanas de marco reducido que llevar a cabo varios paneles.  
  
## <a name="auto-hide-control-bars"></a>Barras de Control de ocultación automática  
 De forma predeterminada, cada `CDockablePane` es compatible con la característica Ocultar automáticamente. Cuando un usuario hace clic en el botón de anclaje en el título de la `CDockablePane`, el marco de trabajo activa el panel en modo de ocultación automática. Para controlar el clic, el marco de trabajo crea un [clase CMFCAutoHideBar](../mfc/reference/cmfcautohidebar-class.md) y un [clase CMFCAutoHideButton](../mfc/reference/cmfcautohidebutton-class.md) asociados con el `CMFCAutoHideBar` objeto. El marco de trabajo coloca la nueva `CMFCAutoHideBar` en el [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md). El marco de trabajo también asocia el `CMFCAutoHideButton` a la barra de herramientas. El [CDockingManager clase](../mfc/reference/cdockingmanager-class.md) mantiene el `CDockablePane`.  
  
## <a name="tabbed-control-bars-and-outlook-bars"></a>Barras de Control con pestañas y barras de Outlook  
 El [CMFCBaseTabCtrl clase](../mfc/reference/cmfcbasetabctrl-class.md) implementa la funcionalidad básica de una ventana con pestañas con pestañas separables. Para usar un `CMFCBaseTabCtrl` de objeto, inicializar un [CBaseTabbedPane (clase)](../mfc/reference/cbasetabbedpane-class.md) en la aplicación. `CBaseTabbedPane` se deriva de `CDockablePane` y mantiene un puntero a un `CMFCBaseTabCtrl` objeto. El `CBaseTabbedPane` permite a los usuarios acoplar y cambiar el tamaño de las barras de control de pestaña. Use [CDockablePane:: Attachtotabwnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd) para crear dinámicamente las barras de control que se acopla y con pestañas.  
  
 El control de barra de Outlook también se basa en las barras con pestañas. El [CMFCOutlookBar (clase)](../mfc/reference/cmfcoutlookbar-class.md) se deriva de `CBaseTabbedPane`. Para obtener más información sobre cómo usar la barra de Outlook, consulte [CMFCOutlookBar (clase)](../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)

