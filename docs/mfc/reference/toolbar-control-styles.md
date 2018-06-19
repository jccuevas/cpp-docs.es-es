---
title: Estilos de Control de barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1958c83ef5a0eec5f3c7f5873451edd3839146be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373200"
---
# <a name="toolbar-control-styles"></a>Estilos de control ToolBar
[Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) tiene un conjunto de indicadores de estilo que determinan la apariencia y comportamiento del botón. Puede establecer una combinación de estas marcas mediante una llamada a [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Este tema enumeran los valores de marca de estilo y sus significados.  
  
## <a name="property-values"></a>Valores de propiedad  
 Los siguientes valores determinan el tipo de botón que representa el control:  
  
 TBBS_BUTTON  
 Pulsador estándar (valor predeterminado).  
  
 TBBS_CHECKBOX  
 casilla de verificación.  
  
 TBBS_CHECKGROUP  
 El inicio de un grupo de casillas de verificación.  
  
 TBBS_GROUP  
 El inicio de un grupo de botones.  
  
 TBBS_SEPARATOR  
 Separador.  
  
 Los valores siguientes representan el estado actual del control:  
  
 TBBS_CHECKED  
 Casilla de verificación está activada.  
  
 TBBS_DISABLED  
 El control está deshabilitado.  
  
 TBBS_INDETERMINATE  
 Casilla de verificación está en un estado indeterminado.  
  
 TBBS_PRESSED  
 Se presionó el botón.  
  
 El valor siguiente cambia el diseño del botón en la barra de herramientas:  
  
 TBBS_BREAK  
 Coloca el elemento en una nueva línea o en una nueva columna sin separación de columnas.  
  
## <a name="remarks"></a>Comentarios  
 El estilo actual se almacena en [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). No establezca un nuevo valor `m_nStyle` directamente, porque algunas clases derivadas realizan otros procesamientos adicionales cuando se llama a `SetStyles`.  
  
 El administrador visual determina la apariencia de los botones en cada estado. Vea [Administrador de visualización](../../mfc/visualization-manager.md) para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Administrador de visualización](../../mfc/visualization-manager.md)


