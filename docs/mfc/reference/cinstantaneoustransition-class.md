---
title: Clase CInstantaneousTransition | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
dev_langs:
- C++
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 9453eee3f872e56bcaaf13c52e37d567df497954
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="cinstantaneoustransition-class"></a>Clase CInstantaneousTransition
Encapsula una transición instantánea.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CInstantaneousTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Construye un objeto de transición e inicializa su valor final.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInstantaneousTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una transición instantánea, el valor de la variable de animación cambia al instante de su valor actual a un valor final especificado. La duración de esta transición siempre es cero. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador de nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="cinstantaneoustransition"></a>CInstantaneousTransition::CInstantaneousTransition  
 Construye un objeto de transición e inicializa su valor final.  
  
```  
CInstantaneousTransition(DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblFinalValue`  
 El valor de la variable de animación al final de la transición.  
  
##  <a name="create"></a>CInstantaneousTransition::Create  
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
 TRUE si la transición se crea correctamente; en caso contrario, FALSE.  
  
##  <a name="m_dblfinalvalue"></a>CInstantaneousTransition::m_dblFinalValue  
 El valor de la variable de animación al final de la transición.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

