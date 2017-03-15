---
title: Clase CConstantTransition | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CConstantTransition
- CConstantTransition
dev_langs:
- C++
helpviewer_keywords:
- CConstantTransition class
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
caps.latest.revision: 17
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: e6c8b8e27cd6618a7dfe690a58ba470a667adf1d
ms.lasthandoff: 02/24/2017

---
# <a name="cconstanttransition-class"></a>Clase CConstantTransition
Encapsula una transición constante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CConstantTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CConstantTransition::CConstantTransition](#cconstanttransition)|Construye un objeto de transición e inicializa su duración.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CConstantTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CConstantTransition::m_duration](#m_duration)|La duración de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una transición constante, el valor de una variable de animación se mantiene en el valor inicial durante la duración de la transición. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CConstantTransition`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-namecconstanttransitiona--cconstanttransitioncconstanttransition"></a><a name="cconstanttransition"></a>CConstantTransition::CConstantTransition  
 Construye un objeto de transición e inicializa su duración.  
  
```  
CConstantTransition (UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
##  <a name="a-namecreatea--cconstanttransitioncreate"></a><a name="create"></a>CConstantTransition::Create  
 Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLibrary`  
 Un puntero a un [IUIAnimationTransitionLibrary interfaz](https://msdn.microsoft.com/library/windows/desktop/dd371897), que define una biblioteca de transiciones estándares.  

### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se crea correctamente; de lo contrario, FALSE.  
  
##  <a name="a-namemdurationa--cconstanttransitionmduration"></a><a name="m_duration"></a>CConstantTransition::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

