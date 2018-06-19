---
title: Proporciona compatibilidad con arrastrar y colocar elementos de encabezado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50cd19d4828269d0591afd0b46768e9917b96906
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349349"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado
Para proporcionar compatibilidad con arrastrar y colocar en elementos de encabezado, especifique el `HDS_DRAGDROP` estilo. Compatibilidad con arrastrar y colocar en elementos de encabezado proporciona al usuario la capacidad para volver a ordenar los elementos de encabezado de un control de encabezado. El comportamiento predeterminado proporciona una imagen de arrastre semitransparente del elemento de encabezado que se están arrastrando y un indicador visual de la nueva posición, si se quita el elemento de encabezado.  
  
 Como con la funcionalidad común de arrastrar y colocar, puede extender el comportamiento de arrastrar y colocar de forma predeterminada controlando el **igual** y **HDN_ENDDRAG** notificaciones. También puede personalizar la apariencia de la imagen de arrastre invalidando el [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) función miembro.  
  
> [!NOTE]
>  Si va a proporcionar compatibilidad con arrastrar y colocar para un control de encabezado incrustado en un control de lista, vea la sección estilo extendido en la [cambiar estilos de Control de lista](../mfc/changing-list-control-styles.md) tema.  
  
## <a name="see-also"></a>Vea también  
 [Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

