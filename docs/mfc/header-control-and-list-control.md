---
title: Control de encabezado y Control de lista | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acee0508243f468f41c645a0cde825ca7c828657
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931599"
---
# <a name="header-control-and-list-control"></a>Control de encabezado y control de lista
En la mayoría de los casos, usará el control de encabezado que está incrustado en un [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) objeto. Sin embargo, hay casos donde un objeto de control de encabezado independiente es deseable, como la manipulación de datos, organizados en filas o columnas, con un [CView](../mfc/reference/cview-class.md)-objeto derivado. En estos casos, necesita mayor control sobre la apariencia y el comportamiento predeterminado de un control de encabezado incrustado.  
  
 En el caso común que desea que un control de encabezado para proporcionar estándar, comportamiento predeterminado, puede querer usar [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) en su lugar. Utilice `CListCtrl` cuando desee que la funcionalidad de un control de encabezado predeterminado, incrustado en un control común de vista de lista. Use [CListView](../mfc/reference/clistview-class.md) cuando desee que la funcionalidad de un control de encabezado predeterminado, incrustado en un objeto de vista.  
  
> [!NOTE]
>  Estos controles sólo incluyen un control de encabezado integrado si el control de vista de lista se crea utilizando el **LVS_REPORT** estilo.  
  
 En la mayoría de los casos, la apariencia del control de encabezado incrustado se puede modificar cambiando los estilos del control de vista de lista que lo contiene. Además, puede obtenerse información sobre el control de encabezado a través de funciones miembro del control de vista de lista primario. Sin embargo, para un control total y acceso a los atributos y estilos del control de encabezado incrustado, se recomienda obtener un puntero al objeto de control de encabezado.  
  
 El objeto de control de encabezado incrustado son accesibles desde `CListCtrl` o `CListView` con una llamada a las respectivas clases `GetHeaderCtrl` función miembro. El código siguiente se muestra cómo hacerlo:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Usar listas de imágenes con controles de encabezado](../mfc/using-image-lists-with-header-controls.md)  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

