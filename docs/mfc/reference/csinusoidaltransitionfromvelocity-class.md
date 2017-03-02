---
title: Clase CSinusoidalTransitionFromVelocity | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromVelocity
- afxanimationcontroller/CSinusoidalTransitionFromVelocity
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity class
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
caps.latest.revision: 18
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
ms.openlocfilehash: 035c92a807fdbe9028547472a3dc816995b95c91
ms.lasthandoff: 02/24/2017

---
# <a name="csinusoidaltransitionfromvelocity-class"></a>Clase CSinusoidalTransitionFromVelocity
Encapsula una transición de progreso sinusoidal cuya amplitud determina el progreso inicial de la variable de animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSinusoidalTransitionFromVelocity : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity](#csinusoidaltransitionfromvelocity)|Construye un objeto de la transición.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::m_duration](#m_duration)|La duración de la transición.|  
|[CSinusoidalTransitionFromVelocity::m_period](#m_period)|El período de oscilación de la onda sinusoidal en segundos.|  
  
## <a name="remarks"></a>Comentarios  
 El valor de la variable de animación oscila alrededor del valor inicial en toda la duración de una transición de intervalo sinusoidal. La amplitud de la oscilación determina el progreso de la variable de animación cuando se inicia la transición. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromVelocity](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-namecreatea--csinusoidaltransitionfromvelocitycreate"></a><a name="create"></a>CSinusoidalTransitionFromVelocity::Create  
 Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLibrary`  
 Puntero a la biblioteca de transición, que es responsable de la creación de transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se crea correctamente; de lo contrario, FALSE.  
  
##  <a name="a-namecsinusoidaltransitionfromvelocitya--csinusoidaltransitionfromvelocitycsinusoidaltransitionfromvelocity"></a><a name="csinusoidaltransitionfromvelocity"></a>CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity  
 Construye un objeto de la transición.  
  
```  
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,  
    UI_ANIMATION_SECONDS period);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
 `period`  
 El período de oscilación de la onda sinusoidal en segundos.  
  
##  <a name="a-namemdurationa--csinusoidaltransitionfromvelocitymduration"></a><a name="m_duration"></a>CSinusoidalTransitionFromVelocity::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="a-namemperioda--csinusoidaltransitionfromvelocitymperiod"></a><a name="m_period"></a>CSinusoidalTransitionFromVelocity::m_period  
 El período de oscilación de la onda sinusoidal en segundos.  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

