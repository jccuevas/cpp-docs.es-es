---
title: Cambiar los estilos de Control de lista | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6758cce9ab42c0dea490dd8ac9803588edceac5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="changing-list-control-styles"></a>Cambiar los estilos de control de lista
Puede cambiar el estilo de ventana de un control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) en cualquier momento después de crearlo. Al cambiar el estilo de ventana, cambiar el tipo de vista que usa el control. Por ejemplo, para emular el explorador, se podrían proporcionar elementos de menú o botones de barra de herramientas para cambiar el control entre las distintas vistas: vista de iconos, vista de lista y así sucesivamente.  
  
 Por ejemplo, cuando el usuario selecciona el elemento de menú, que podría realizar una llamada a [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) para recuperar el estilo del control actual y, a continuación, llame a [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) para restablecer el estilo. Para obtener más información, consulte [mediante controles de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774736) del SDK de Windows.  
  
 Estilos disponibles están enumerados en [crear](../mfc/reference/clistctrl-class.md#create). Los estilos `LVS_ICON`, `LVS_SMALLICON`, `LVS_LIST`, y `LVS_REPORT` designar las vistas de control de cuatro lista.  
  
## <a name="extended-styles"></a>Estilos extendidos  
 Además de los estilos estándares para un control de lista, hay otro conjunto, que se conoce como estilos extendidos. Estos estilos, descritos en [estilos extendidos de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774732) del SDK de Windows, ofrecen una variedad de características útiles que personalizan el comportamiento del control de lista. Para implementar el comportamiento de un estilo determinado (por ejemplo, la selección al mantener el mouse), realice una llamada a [CListCtrl:: SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), pasa el estilo necesario. En el ejemplo siguiente se muestra la llamada de función:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  Para que funcione la selección al mantener el mouse, también debe tener una **LVS_EX_ONECLICKACTIVATE** o **LVS_EX_TWOCLICKACTIVATE** activado.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

