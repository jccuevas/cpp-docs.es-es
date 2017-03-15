---
title: Clase CCubicTransition | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCubicTransition
- afxanimationcontroller/CCubicTransition
dev_langs:
- C++
helpviewer_keywords:
- CCubicTransition class
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
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
ms.openlocfilehash: 511dc175d51db7887a462aaf63f4f91290375751
ms.lasthandoff: 02/24/2017

---
# <a name="ccubictransition-class"></a>Clase CCubicTransition
Encapsula una transición cúbica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCubicTransition::CCubicTransition](#ccubictransition)|Construye un objeto de transición e inicializa sus parámetros.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCubicTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la animación al final de la transición.|  
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|La velocidad de la variable al final de la transición.|  
|[CCubicTransition::m_duration](#m_duration)|La duración de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una transición cúbica, el valor de la variable de animación cambia su valor inicial a un valor final especificado durante la duración de la transición, terminando en una velocidad especificada. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCubicTransition`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-nameccubictransitiona--ccubictransitionccubictransition"></a><a name="ccubictransition"></a>CCubicTransition::CCubicTransition  
 Construye un objeto de transición e inicializa sus parámetros.  
  
```  
CCubicTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE finalVelocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
 `finalValue`  
 El valor de la animación al final de la transición.  
  
 `finalVelocity`  
 La velocidad de la variable al final de la transición.  
  
##  <a name="a-namecreatea--ccubictransitioncreate"></a><a name="create"></a>CCubicTransition::Create  
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
  
##  <a name="a-namemdblfinalvaluea--ccubictransitionmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue  
 El valor de la animación al final de la transición.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemdblfinalvelocitya--ccubictransitionmdblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity  
 La velocidad de la variable al final de la transición.  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
##  <a name="a-namemdurationa--ccubictransitionmduration"></a><a name="m_duration"></a>CCubicTransition::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

