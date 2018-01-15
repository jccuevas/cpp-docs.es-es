---
title: Agregar elementos al Control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d117aa06f82da1024d11af38cc4277916c6bca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-items-to-the-control"></a>Agregar elementos al control
Para agregar elementos al control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)), llame a uno de las versiones de la [InsertItem](../mfc/reference/clistctrl-class.md#insertitem) función de miembro, dependiendo de qué información tienen. Una versión toma un [LV_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760) estructura que prepare. Dado que el `LV_ITEM` estructura contiene muchos miembros, tener un mayor control sobre los atributos del elemento de control de lista.  
  
 Dos miembros importantes (con respecto a la vista de informe) de la `LV_ITEM` estructura son el `iItem` y `iSubItem` los miembros. El `iItem` miembro es el índice de base cero del elemento que se hace referencia la estructura y el `iSubItem` miembro es el índice basado en uno de un subelemento, o cero si la estructura contiene información sobre un elemento. Con estos dos miembros se determina, por elemento, el tipo y valor de información del subelemento que se muestra cuando el control de lista está en vista de informe. Para obtener más información, consulte [CListCtrl:: SetItem](../mfc/reference/clistctrl-class.md#setitem).  
  
 Miembros adicionales que especifican el elemento texto, icono, estado y datos de elemento. "Elemento de datos" es un valor definido por la aplicación asociado a un elemento de vista de lista. Para obtener más información sobre la `LV_ITEM` estructura, vea [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem).  
  
 Otras versiones de `InsertItem` tomar uno o más valores independientes, correspondientes a los miembros de la `LV_ITEM` estructura, lo que permite inicializar solo aquellos miembros que desee admitir. Por lo general, el control de lista administra el almacenamiento para los elementos de lista, pero puede almacenar parte de la información en la aplicación en su lugar, mediante "elementos de devolución de llamada". Para obtener más información, consulte [elementos de devolución de llamada y la máscara de devolución de llamada](../mfc/callback-items-and-the-callback-mask.md) en este tema y [elementos de devolución de llamada y la máscara de devolución de llamada](http://msdn.microsoft.com/library/windows/desktop/bb774736) en el SDK de Windows.  
  
 Para obtener más información, consulte [agregar elementos de vista de lista y subelementos](http://msdn.microsoft.com/library/windows/desktop/bb774736).  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

