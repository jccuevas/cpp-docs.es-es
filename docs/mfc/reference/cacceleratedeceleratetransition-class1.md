---
title: CAccelerateDecelerateTransition Class1 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
dev_langs:
- C++
helpviewer_keywords:
- CAccelerateDecelerateTransition class
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f11dc96b48695b998fb17c33735e8f56bce517b7
ms.lasthandoff: 02/24/2017

---
# <a name="cacceleratedeceleratetransition-class"></a>Clase CAccelerateDecelerateTransition
Implementa una transición que aumenta/reduce la velocidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Construye un objeto de la transición.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|La proporción del tiempo transcurrido acelerando la duración.|  
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|La proporción del tiempo dedicado a disminuir la velocidad a la duración.|  
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|La duración de la transición.|  
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|El valor de la animación al final de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una-reducir la velocidad de transición, la variable de animación acelera y ralentiza durante la duración de la transición, terminando en un valor especificado. Puede controlar la rapidez con la variable acelera y ralentiza de forma independiente, mediante la especificación de aceleración diferentes proporciones de desaceleración. Cuando la velocidad inicial es cero, la proporción de aceleración es la fracción de la duración de la variable pasará la aceleración; del mismo modo con la proporción de desaceleración. Si la velocidad inicial es distinto de cero, es la fracción del tiempo entre la velocidad llegue a cero y el final de la transición. La proporción de aceleración y la desaceleración deben ser igual a un máximo de 1.0. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CAccelerateDecelerateTransition`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-namecacceleratedeceleratetransitiona--cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition  
 Construye un objeto de la transición.  
  
```  
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE accelerationRatio = 0.3,  
    DOUBLE decelerationRatio = 0.3);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
 `finalValue`  
 El valor de la animación al final de la transición.  
  
 `accelerationRatio`  
 La proporción del tiempo transcurrido acelerando la duración.  
  
 `decelerationRatio`  
 La proporción del tiempo dedicado a disminuir la velocidad a la duración.  
  
##  <a name="a-namecreatea--cacceleratedeceleratetransitioncreate"></a><a name="create"></a>CAccelerateDecelerateTransition::Create  
 Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* *\not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
`pLibrary`  
 Un puntero a un [IUIAnimationTransitionLibrary interfaz](https://msdn.microsoft.com/library/windows/desktop/dd371897), que define una biblioteca de transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se crea correctamente; de lo contrario, FALSE.  
  
##  <a name="a-namemaccelerationratioa--cacceleratedeceleratetransitionmaccelerationratio"></a><a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio  
 La proporción del tiempo transcurrido acelerando la duración.  
  
```  
DOUBLE m_accelerationRatio;  
```  
  
##  <a name="a-namemdecelerationratioa--cacceleratedeceleratetransitionmdecelerationratio"></a><a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio  
 La proporción del tiempo dedicado a disminuir la velocidad a la duración.  
  
```  
DOUBLE m_decelerationRatio;  
```  
  
##  <a name="a-namemdurationa--cacceleratedeceleratetransitionmduration"></a><a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="a-namemfinalvaluea--cacceleratedeceleratetransitionmfinalvalue"></a><a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue  
 El valor de la animación al final de la transición.  
  
```  
DOUBLE m_finalValue;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

