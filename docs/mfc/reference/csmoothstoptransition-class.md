---
title: Clase CSmoothStopTransition | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
dev_langs:
- C++
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: d990cfda954ef11707cd8d8fe8612e75467a1be0
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="csmoothstoptransition-class"></a>Clase CSmoothStopTransition
Encapsula una transición de pausa suavizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSmoothStopTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|Construye una transición de pausa suavizada e inicializa su duración máxima y el valor final.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSmoothStopTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|  
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|La duración máxima de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Una transición de pausa suavizada se ralentiza puesto que un determinado valor final aproxima y llega a dicha cola con una velocidad de cero. La duración de la transición viene determinada por el progreso inicial, la diferencia entre los valores iniciales y finales y el tiempo máximo especificado. Si no hay ninguna solución que consta de un único arco parabólica, este método crea una transición cúbica. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador de nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="create"></a>CSmoothStopTransition::Create  
 Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLibrary`  
 Un puntero a la biblioteca de transición, que es responsable de la creación de transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se crea correctamente; en caso contrario, FALSE.  
  
##  <a name="csmoothstoptransition"></a>CSmoothStopTransition::CSmoothStopTransition  
 Construye una transición de pausa suavizada e inicializa su duración máxima y el valor final.  
  
```  
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `maximumDuration`  
 La duración máxima de la transición.  
  
 `dblFinalValue`  
 El valor de la variable de animación al final de la transición.  
  
##  <a name="m_dblfinalvalue"></a>CSmoothStopTransition::m_dblFinalValue  
 El valor de la variable de animación al final de la transición.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_maximumduration"></a>CSmoothStopTransition::m_maximumDuration  
 La duración máxima de la transición.  
  
```  
UI_ANIMATION_SECONDS m_maximumDuration;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

