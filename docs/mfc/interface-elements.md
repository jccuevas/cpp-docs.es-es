---
title: Elementos de la interfaz
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 4d4d81287cb30a7d3608025085cdb3f9a208147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619994"
---
# <a name="interface-elements"></a>Elementos de la interfaz

En este documento se describen los elementos de interfaz que se introdujeron en Visual Studio 2008 SP1 y también se describen las diferencias con la versión anterior de la biblioteca.

En la ilustración siguiente se muestra una aplicación que se compiló con los nuevos elementos de la interfaz.

![Aplicación de ejemplo de MFC Feature Pack](../mfc/media/mfc_featurepack.png "Aplicación de ejemplo de MFC Feature Pack")

## <a name="window-docking"></a>Acoplamiento de ventanas

La funcionalidad de acoplamiento de ventanas se parece al acoplamiento de ventanas que usa la interfaz gráfica de usuario de Visual Studio.

## <a name="control-bars-are-now-panes"></a>Las barras de control son ahora paneles

Las barras de control se conocen ahora como paneles y se derivan de la [clase a cbasepane](reference/cbasepane-class.md). En versiones anteriores de MFC, la clase base de las barras de control era `CControlBar` .

La ventana de marco principal de la aplicación se representa normalmente mediante la [clase CFrameWndEx](reference/cframewndex-class.md) o la [clase cmdiframewndex (](reference/cmdiframewndex-class.md). El marco principal se denomina *sitio de acoplamiento*. Los paneles pueden tener uno de estos tres tipos de elementos primarios: un sitio de acoplamiento, una barra de acoplamiento o una ventana de marco reducido.

Hay dos tipos de paneles: no se pueden cambiar de tamaño y cambiar de tamaño. Se puede cambiar el tamaño de los paneles de tamaño variable, como barras de estado y barras de herramientas, mediante separadores o controles deslizantes. Los paneles de tamaño variable pueden formar contenedores (un panel se puede acoplar a otro panel, creando un divisor entre ellos). Sin embargo, los paneles de tamaño variable no se pueden adjuntar (acoplar) a las barras de acoplamiento.

Si la aplicación usa paneles que no se puedan cambiar de tamaño, derivelos de la [clase CPane](reference/cpane-class.md).  Si la aplicación usa paneles de tamaño variable, derivelos de la [clase CDockablePane](reference/cdockablepane-class.md)

## <a name="dock-site"></a>Sitio de Dock

El sitio de acoplamiento (o la ventana de marco principal) posee todos los paneles y ventanas de marco reducido en una aplicación. El sitio de acoplamiento contiene un miembro de [CDockingManager](reference/cdockingmanager-class.md) . Este miembro mantiene una lista de todos los paneles que pertenecen al sitio de acoplamiento. La lista está ordenada de forma que los paneles creados en los bordes exteriores del sitio de acoplamiento se coloquen al principio de la lista. Cuando el marco vuelve a dibujar el sitio de acoplamiento, recorre en iteración esta lista y ajusta el diseño de cada panel para incluir el rectángulo delimitador actual del sitio de acoplamiento. Puede llamar a `AdjustDockingLayout` o `RecalcLayout` cuando tenga que ajustar el diseño de acoplamiento y el marco redirige esta llamada al administrador de acoplamiento.

## <a name="dock-bars"></a>Barras de acoplamiento

Cada ventana de marco principal puede colocar las *barras de acoplamiento* a lo largo de los bordes. Una barra de acoplamiento es un panel que pertenece a una [clase CDockSite](reference/cdocksite-class.md). Las barras de acoplamiento pueden aceptar objetos derivados de [CPane](reference/cpane-class.md), como las barras de herramientas. Para crear barras de acoplamiento cuando se inicializa la ventana de marco principal, llame a `EnableDocking` . Para habilitar las barras de ocultación automática, llame a `EnableAutoHideBars` . `EnableAutoHideBars`crea objetos [CAutoHideDockSite](reference/cautohidedocksite-class.md) y los coloca junto a cada barra de acoplamiento.

Cada barra de acoplamiento se divide en acoplar filas. Las filas de acoplamiento se representan mediante la [clase CDockingPanesRow](reference/cdockingpanesrow-class.md). Cada fila de acoplamiento contiene una lista de barras de herramientas. Si un usuario acopla una barra de herramientas o mueve la barra de herramientas de una fila a otra dentro de la misma barra de acoplamiento, el marco de trabajo crea una nueva fila y cambia el tamaño de la barra de acoplamiento en consecuencia, o bien coloca la barra de herramientas en una fila existente.

## <a name="mini-frame-windows"></a>Ventanas de marco reducido

Un panel flotante reside en una ventana de marco reducido. Las ventanas de marco reducido se representan mediante dos clases: [clase CMDITabInfo](reference/cmditabinfo-class.md) (que solo puede contener un panel) y [clase CMultiPaneFrameWnd](reference/cmultipaneframewnd-class.md) (que puede contener varios paneles). Para flotar un panel en el código, llame a [a cbasepane:: FloatPane](reference/cbasepane-class.md#floatpane). Una vez que un panel flota, el marco de trabajo crea automáticamente una ventana de marco reducido y la ventana de marco reducido se convierte en el elemento primario del panel flotante. Cuando el panel flotante se acopla, el marco de trabajo restablece su elemento primario y el panel flotante se convierte en una barra de acoplamiento (para las barras de herramientas) o en un sitio de acoplamiento (para los paneles de tamaño variable).

## <a name="pane-dividers"></a>Divisores de paneles

Los divisores de paneles (también denominados controles deslizantes o divisores) se representan mediante la [clase CPaneDivider](reference/cpanedivider-class.md). Cuando un usuario acopla un panel, el marco crea divisores del panel, independientemente de si el panel está acoplado en el sitio de acoplamiento o en otro panel. Cuando un panel se acopla al sitio de acoplamiento, el divisor del panel se denomina el *divisor del panel predeterminado*. El divisor del panel predeterminado es responsable del diseño de todos los paneles de acoplamiento en el sitio de Docker. Dock Manager mantiene una lista de los divisores de paneles predeterminados y una lista de paneles. Los administradores de Dock son responsables del diseño de todos los paneles de acoplamiento.

## <a name="containers"></a>Contenedores

Todos los paneles de tamaño variable, cuando se acoplan entre sí, se mantienen en contenedores. Los contenedores se representan mediante la [clase CPaneContainer](reference/cpanecontainer-class.md). Cada contenedor tiene punteros al panel izquierdo, al panel derecho, al subcontenedor izquierdo, al subcontenedor derecho y al divisor entre las partes izquierda y derecha. (*Izquierda* y *derecha* no hacen referencia a los lados físicos, sino que identifican las ramas de una estructura de árbol). De esta manera, podemos crear un árbol de paneles y separadores y, por tanto, lograr diseños complejos de paneles que se pueden cambiar de tamaño. La `CPaneContainer` clase mantiene el árbol de contenedores; también mantiene dos listas de paneles y controles deslizantes que residen en este árbol. Los administradores de contenedores de paneles normalmente se incrustan en los controles deslizantes predeterminados y las ventanas de marco reducido que incluyen varios paneles.

## <a name="auto-hide-control-bars"></a>Ocultar automáticamente barras de control

De forma predeterminada, cada `CDockablePane` admite la característica de ocultación automática. Cuando un usuario hace clic en el botón anclar del título de la `CDockablePane` , el marco de trabajo cambia el panel al modo de ocultación automática. Para controlar el clic, el marco de trabajo crea una [clase CMFCAutoHideBar](reference/cmfcautohidebar-class.md) y una [clase CMFCAutoHideButton](reference/cmfcautohidebutton-class.md) asociada al `CMFCAutoHideBar` objeto. El marco de trabajo coloca el nuevo `CMFCAutoHideBar` en el [CAutoHideDockSite](reference/cautohidedocksite-class.md). El marco también asocia `CMFCAutoHideButton` a la barra de herramientas. La [clase CDockingManager](reference/cdockingmanager-class.md) mantiene el `CDockablePane` .

## <a name="tabbed-control-bars-and-outlook-bars"></a>Barras de control con pestañas y barras de Outlook

La [clase CMFCBaseTabCtrl](reference/cmfcbasetabctrl-class.md) implementa la funcionalidad básica de una ventana con pestañas con pestañas desconectables. Para usar un `CMFCBaseTabCtrl` objeto, inicialice una [clase CBaseTabbedPane](reference/cbasetabbedpane-class.md) en la aplicación. `CBaseTabbedPane`se deriva de `CDockablePane` y mantiene un puntero a un `CMFCBaseTabCtrl` objeto. `CBaseTabbedPane`Permite a los usuarios acoplar y cambiar el tamaño de las barras de control con pestañas. Use [CDockablePane:: AttachToTabWnd](reference/cdockablepane-class.md#attachtotabwnd) para crear dinámicamente barras de control acopladas y con pestañas.

El control de barra de Outlook también se basa en las barras de pestañas. La [clase cmfcoutlookbar (](reference/cmfcoutlookbar-class.md) se deriva de `CBaseTabbedPane` . Para obtener más información sobre cómo usar la barra de Outlook, consulte [clase cmfcoutlookbar (](reference/cmfcoutlookbar-class.md).

## <a name="see-also"></a>Consulte también

[Conceptos](mfc-concepts.md)
