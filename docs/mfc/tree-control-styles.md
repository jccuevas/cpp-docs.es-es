---
title: Estilos de Control de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a448d76236c3467228b2aa57cd71284274687ac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200436"
---
# <a name="tree-control-styles"></a>Estilos de control de árbol
Control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) estilos controlan aspectos de la apariencia de un control de árbol. Establece los estilos iniciales al crear el control de árbol. Puede recuperar y cambiar los estilos de una vez creado el control de árbol mediante el [GetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633584) y [SetWindowLong](https://msdn.microsoft.com/library/windows/desktop/ms633591) las funciones de Windows, especificar **GWL_STYLE** para el *nIndex* parámetro. Para obtener una lista completa de los estilos, consulte [estilos de ventana de Control de vista de árbol](/windows/desktop/Controls/tree-view-control-window-styles) en el SDK de Windows.  
  
 El **TVS_HASLINES** estilo mejora la representación gráfica de la jerarquía de un control de árbol mediante el dibujo de líneas que vinculan elementos secundarios a su elemento primario correspondiente. Este estilo no vincular elementos en la raíz de la jerarquía. Para ello, necesita combinar el **TVS_HASLINES** y **TVS_LINESATROOT** estilos.  
  
 El usuario puede expandir o contraer la lista de un elemento primario de los elementos secundarios haciendo doble clic en el elemento primario. Un control de árbol que tiene el **TVS_SINGLEEXPAND** estilo hace que el elemento seleccionado se expanda y el elemento no seleccionado se contraiga. Si el mouse se usa para el elemento seleccionado de un solo clic y ese elemento se cierra, se expandirá. Si el elemento seleccionado se hace clic único cuando se abre, se contraerá.  
  
 Un control de árbol que tiene el **TVS_HASBUTTONS** estilo agrega un botón a la izquierda de cada elemento primario. El usuario puede hacer clic en el botón para expandir o contraer los elementos secundarios como alternativa al hacer doble clic en el elemento primario. **TVS_HASBUTTONS** no agregar botones a elementos en la raíz de la jerarquía. Para ello, debe combinar **TVS_HASLINES**, **TVS_LINESATROOT**, y **TVS_HASBUTTONS**.  
  
 El **TVS_EDITLABELS** estilo hace posible que el usuario editar las etiquetas de elementos de control de árbol. Para obtener más información acerca de cómo editar las etiquetas, consulte [edición de la etiqueta de Control de árbol](../mfc/tree-control-label-editing.md) más adelante en este tema.  
  
 El **TVS_NOTOOLTIPS** estilo deshabilita la característica de sugerencia de la herramienta automática de los controles de vista de árbol. Esta característica muestra automáticamente una información sobre herramientas, que contiene el título del elemento bajo el cursor del mouse, si todo el título no está actualmente visible.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

