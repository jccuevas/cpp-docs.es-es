---
title: Clase CMFCDisableMenuAnimation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation class
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 22
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ea0be944ca70d6f8317fd4bc60fdd50ecc714438
ms.lasthandoff: 02/24/2017

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
|Nombre|Descripción|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Construye un objeto `CMFCDisableMenuAnimation`.|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCDisableMenuAnimation::Restore](#restore)|Restaura la animación anterior que el marco de trabajo que se utiliza para mostrar un menú emergente.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|`CMFCDisableMenuAnimation::m_animType`|Almacena el tipo de animación anterior menú emergente.|  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta clase auxiliar para deshabilitar temporalmente la animación de menús emergentes (por ejemplo, al procesar los comandos de mouse o teclado).  
  
 Un `CMFCDisableMenuAnimation` objeto deshabilita la animación de menús emergentes durante su duración. El constructor almacena el tipo actual de animación de menús emergentes en el `m_animType` campo y establece el tipo de la animación actual a `CMFCPopupMenu::NO_ANIMATION`. El destructor restaura el tipo de animación anterior.  
  
 Puede crear un `CMFCDisableMenuAnimation` objeto en la pila para deshabilitar la animación de menús emergentes en una sola función. Si desea deshabilitar la animación de menús emergentes entre funciones, crear un `CMFCDisableMenuAnimation` en el montón de objeto y, a continuación, eliminarlo cuando desee restaurar la animación de menús emergentes.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar la pila para deshabilitar temporalmente la animación de menús.  
  
 [!code-cpp[1 NVC_MFC_Misc](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpopupmenu.h  
  
##  <a name="restore"></a>CMFCDisableMenuAnimation::Restore  
 Restaura la animación anterior que el marco de trabajo que se utiliza para mostrar un menú emergente.  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por el `CMFCDisableMenuAnimation` destructor para restaurar la animación anterior que el marco de trabajo que se utiliza para mostrar un menú emergente.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

