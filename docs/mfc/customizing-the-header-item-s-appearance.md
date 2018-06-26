---
title: Personalizar el elemento de encabezado&#39;s apariencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e09f8bc0b61e22435ee348968f117940b57132e3
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930880"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personalizar el elemento de encabezado&#39;s apariencia
Estableciendo la *dwStyle* parámetro cuando se crea un control de encabezado ([CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create)), puede definir la apariencia y comportamiento del encabezado de elementos o del encabezado del control.  
  
 Este es un muestreo de los estilos que se puede establecer y su propósito:  
  
-   Para hacer que un elemento de encabezado parezca un botón de comando, use la **HDS_BUTTONS** estilo.  
  
     Utilice este estilo si desea llevar a cabo acciones en respuesta a los clics del mouse (ratón) en un elemento de encabezado, como ordenar datos en una columna determinada, tal y como se hace en Microsoft Outlook.  
  
-   Para conceder a los elementos de encabezado una apariencia de "seguimiento activo" cuando el cursor del mouse pasa sobre ellas, utilice el **HDS_HOTTRACK** estilo.  
  
     Seguimiento activo muestra un contorno 3D a medida que pasa el puntero sobre un elemento en un plano en caso contrario, barra.  
  
-   Para indicar que debe estar oculta el control de encabezado, utilice la **HDS_HIDDEN** estilo.  
  
     El **HDS_HIDDEN** estilo indica que el control de encabezado está diseñado para usarse como un contenedor de datos y no es un control visual. Este estilo no oculta automáticamente el control pero, en su lugar, afecta al comportamiento de `CHeaderCtrl::Layout`. El valor devuelto en el *cy* miembro de la `WINDOWPOS` estructura será cero que indica que el control no debería estar visible para el usuario.  
  
 Para obtener más información acerca de estas propiedades, vea [elementos](http://msdn.microsoft.com/library/windows/desktop/bb775238) del SDK de Windows. Para obtener información sobre cómo agregar elementos a un control de encabezado, vea [agregar elementos al Control de encabezado](../mfc/adding-items-to-the-header-control.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

