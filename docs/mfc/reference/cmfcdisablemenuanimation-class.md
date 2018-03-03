---
title: Clase CMFCDisableMenuAnimation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 458a35e708db41ee393da70aedd653aca44cf802
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdisablemenuanimation-class"></a>Clase CMFCDisableMenuAnimation
Deshabilita la animación de menús emergentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Construye un objeto `CMFCDisableMenuAnimation`.|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCDisableMenuAnimation::Restore](#restore)|Restaura la animación anterior que usa el marco de trabajo para mostrar un menú emergente.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|nombre|Descripción|  
|`CMFCDisableMenuAnimation::m_animType`|Almacena el tipo de animación del menú emergente anterior.|  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta clase auxiliar para deshabilitar temporalmente la animación de menús emergentes (por ejemplo, al procesar comandos del mouse o teclado).  
  
 Un `CMFCDisableMenuAnimation` objeto deshabilita la animación de menús emergentes durante su duración. El constructor almacena el tipo actual de animación de menús emergentes en el `m_animType` campo y establece el tipo de la animación actual a `CMFCPopupMenu::NO_ANIMATION`. El destructor restaura el tipo de animación anterior.  
  
 Puede crear un `CMFCDisableMenuAnimation` objeto en la pila para deshabilitar la animación de menús emergentes a lo largo de una sola función. Si desea deshabilitar la animación de menús emergentes entre funciones, cree una `CMFCDisableMenuAnimation` en el montón de objetos y, a continuación, eliminarlo si desea restaurar la animación de menús emergentes.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar la pila para deshabilitar temporalmente la animación de menús.  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpopupmenu.h  
  
##  <a name="restore"></a>CMFCDisableMenuAnimation::Restore  
 Restaura la animación anterior que usa el marco de trabajo para mostrar un menú emergente.  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por el `CMFCDisableMenuAnimation` destructor para restaurar la animación anterior que usa el marco de trabajo para mostrar un menú emergente.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)
