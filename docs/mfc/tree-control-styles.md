---
title: Estilos de Control de árbol | Documentos de Microsoft
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
ms.openlocfilehash: 3c0158bfc24eb86f88695b58943989fbb7cac435
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-styles"></a>Estilos de control de árbol
Control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) estilos controlan aspectos de la apariencia de un control de árbol. Establecer los estilos iniciales cuando se crea el control de árbol. Puede recuperar y cambiar los estilos después de crear el control de árbol utilizando la [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) y [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) funciones de Windows, especificar **GWL_STYLE** para el `nIndex` parámetro. Para obtener una lista completa de los estilos, consulte [estilos de ventana de Control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760013) del SDK de Windows.  
  
 El **TVS_HASLINES** estilo mejora la representación gráfica de la jerarquía de un control de árbol dibujando líneas que vinculan los elementos secundarios a su elemento primario correspondiente. Este estilo no vincula a elementos en la raíz de la jerarquía. Para ello, necesita combinar el **TVS_HASLINES** y **TVS_LINESATROOT** estilos.  
  
 El usuario puede expandir o contraer la lista de elementos secundarios del elemento de un primario haciendo doble clic en el elemento primario. Un control de árbol que contiene el **TVS_SINGLEEXPAND** estilo hace que el elemento seleccionado se expanda y el elemento que se va a anular la selección para contraer. Si el mouse se utiliza para el elemento seleccionado con un solo clic y ese elemento está cerrado, se expandirán. Si el elemento seleccionado se hace clic solo cuando se abre, se contraen.  
  
 Un control de árbol que contiene el **TVS_HASBUTTONS** estilo agrega un botón a la izquierda de cada elemento primario. El usuario puede hacer clic en el botón para expandir o contraer los elementos secundarios como alternativa al hacer doble clic en el elemento primario. **TVS_HASBUTTONS** no agregar botones a elementos en la raíz de la jerarquía. Para ello, debe combinar **TVS_HASLINES**, **TVS_LINESATROOT**, y **TVS_HASBUTTONS**.  
  
 El **TVS_EDITLABELS** estilo hace posible para el usuario editar las etiquetas de elementos de control de árbol. Para obtener más información acerca de cómo editar las etiquetas, vea [edición de la etiqueta de Control de árbol](../mfc/tree-control-label-editing.md) más adelante en este tema.  
  
 El **TVS_NOTOOLTIPS** estilo deshabilita la característica de sugerencia de herramienta automática de los controles de vista de árbol. Esta característica muestra automáticamente la información sobre herramientas que contiene el título del elemento en el cursor del mouse, si todo el título no es visible en ese momento.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

