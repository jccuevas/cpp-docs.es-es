---
title: CLinearTransition (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64b53cafc60e556ac142cdaf1f56608e5ab3de70
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211746"
---
# <a name="clineartransition-class"></a>Clase CLinearTransition
Encapsula una transición lineal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CLinearTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransition::CLinearTransition](#clineartransition)|Construye un objeto de transición lineal y lo inicializa con la duración y el valor final.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|  
|[CLinearTransition::m_duration](#m_duration)|La duración de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una transición lineal, el valor de la variable de animación realiza la transición linealmente desde su valor inicial para un valor final especificado. Dado que todas las transiciones se borran automáticamente, se recomienda asignada a ellos mediante el operador nuevo. El objeto COM IUIAnimationTransition encapsulado se crea por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransition](../../mfc/reference/clineartransition-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="clineartransition"></a>  CLinearTransition::CLinearTransition  
 Construye un objeto de transición lineal y lo inicializa con la duración y el valor final.  
  
```  
CLinearTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *Duración*  
 La duración de la transición.  
  
 *dblFinalValue*  
 El valor de la variable de animación al final de la transición.  
  
##  <a name="create"></a>  CLinearTransition::Create  
 Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
*pLibrary*  
 Un puntero a un [IUIAnimationTransitionLibrary interfaz](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se crea correctamente; en caso contrario, FALSE.  
  
##  <a name="m_dblfinalvalue"></a>  CLinearTransition::m_dblFinalValue  
 El valor de la variable de animación al final de la transición.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_duration"></a>  CLinearTransition::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
