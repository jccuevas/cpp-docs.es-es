---
title: Estilos de Control de barra de herramientas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1c50009a50c5b80e007add9de679315df6aecea9
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="toolbar-control-styles"></a>Estilos de control ToolBar
[Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) tiene un conjunto de indicadores de estilo que determinan el aspecto y el comportamiento del botón. Puede establecer una combinación de estas marcas llamando [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Este tema enumeran los valores de indicador de estilo y sus significados.  
  
## <a name="property-values"></a>Valores de propiedades  
 Los siguientes valores determinan el tipo de botón que representa el control:  
  
 TBBS_BUTTON  
 Botón de comando estándar (predeterminado).  
  
 TBBS_CHECKBOX  
 Casilla de verificación.  
  
 TBBS_CHECKGROUP  
 El inicio de un grupo de casillas de verificación.  
  
 TBBS_GROUP  
 Inicio de un grupo de botones.  
  
 TBBS_SEPARATOR  
 Separador.  
  
 Los valores siguientes representan el estado actual del control:  
  
 TBBS_CHECKED  
 Casilla de verificación está activada.  
  
 TBBS_DISABLED  
 Control está deshabilitado.  
  
 TBBS_INDETERMINATE  
 Casilla de verificación está en un estado indeterminado.  
  
 TBBS_PRESSED  
 Se presionó el botón.  
  
 El valor siguiente cambia el diseño del botón de la barra de herramientas:  
  
 TBBS_BREAK  
 Coloca el elemento en una nueva línea o en una nueva columna sin separar las columnas.  
  
## <a name="remarks"></a>Comentarios  
 El estilo actual se almacena en [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). No establezca un nuevo valor en `m_nStyle` directamente, ya que algunas clases derivadas realizan un procesamiento adicional cuando se llama a `SetStyles`.  
  
 El administrador visual determina la apariencia de los botones en cada estado. Consulte [Administrador de visualización](../../mfc/visualization-manager.md) para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Administrador de visualización](../../mfc/visualization-manager.md)



