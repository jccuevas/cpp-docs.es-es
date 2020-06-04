---
title: Estilos de control de árbol
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510940"
---
# <a name="tree-control-styles"></a>Estilos de control de árbol

Los estilos de control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) rigen aspectos de la apariencia de un control de árbol. Los estilos iniciales se establecen al crear el control de árbol. Puede recuperar y cambiar los estilos después de crear el control de árbol mediante las funciones de Windows [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) y [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) , especificando **GWL_STYLE** para el parámetro *NINDEX* . Para obtener una lista completa de estilos, vea estilos de la [ventana de control de vista de árbol](/windows/win32/Controls/tree-view-control-window-styles) en el Windows SDK.

El estilo **TVS_HASLINES** mejora la representación gráfica de la jerarquía de un control de árbol mediante el dibujo de líneas que vinculan los elementos secundarios con el elemento primario correspondiente. Este estilo no vincula elementos en la raíz de la jerarquía. Para ello, debe combinar los estilos **TVS_HASLINES** y **TVS_LINESATROOT** .

El usuario puede expandir o contraer la lista de elementos secundarios de un elemento primario haciendo doble clic en el elemento primario. Un control de árbol que tenga el estilo **TVS_SINGLEEXPAND** hace que se seleccione expandir el elemento y que el elemento que se va a anular la selección se contraiga. Si el mouse se usa para hacer un solo clic en el elemento seleccionado y dicho elemento está cerrado, se expandirá. Si se hace un solo clic en el elemento seleccionado cuando está abierto, se contraerá.

Un control de árbol con el estilo **TVS_HASBUTTONS** agrega un botón al lado izquierdo de cada elemento primario. El usuario puede hacer clic en el botón para expandir o contraer los elementos secundarios como alternativa a hacer doble clic en el elemento primario. **TVS_HASBUTTONS** no agrega botones a los elementos de la raíz de la jerarquía. Para ello, debe combinar **TVS_HASLINES**, **TVS_LINESATROOT**y **TVS_HASBUTTONS**.

El estilo **TVS_EDITLABELS** permite al usuario editar las etiquetas de los elementos de control de árbol. Para obtener más información sobre la edición de etiquetas, vea [edición de etiquetas de control de árbol](../mfc/tree-control-label-editing.md) más adelante en este tema.

El estilo **TVS_NOTOOLTIPS** deshabilita la característica de información sobre herramientas automática de los controles de vista de árbol. Esta característica muestra automáticamente una información sobre herramientas, que contiene el título del elemento bajo el cursor del mouse, si el título completo no está actualmente visible.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
