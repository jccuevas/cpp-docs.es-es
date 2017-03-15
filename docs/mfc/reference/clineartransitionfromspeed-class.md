---
title: Clase CLinearTransitionFromSpeed | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransitionFromSpeed class
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
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
ms.openlocfilehash: b96ed05e0fbed5fdb6d384f49ca634b4bc7d9269
ms.lasthandoff: 02/24/2017

---
# <a name="clineartransitionfromspeed-class"></a>Clase CLinearTransitionFromSpeed
Encapsula una transición de velocidad lineal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Construye un objeto de la transición de velocidad lineal y lo inicializa con la velocidad y el valor final.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|El valor de la animación al final de la transición.|  
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|El valor absoluto de la velocidad de la variable.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una transición de velocidad lineal cambia el valor de la variable de animación a una velocidad especificada. La duración de la transición viene determinada por la diferencia entre el valor inicial y el valor final especificado. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-nameclineartransitionfromspeeda--clineartransitionfromspeedclineartransitionfromspeed"></a><a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed::CLinearTransitionFromSpeed  
 Construye un objeto de la transición de velocidad lineal y lo inicializa con la velocidad y el valor final.  
  
```  
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblSpeed`  
 El valor absoluto de la velocidad de la variable.  
  
 `dblFinalValue`  
 El valor de la animación al final de la transición.  
  
##  <a name="a-namecreatea--clineartransitionfromspeedcreate"></a><a name="create"></a>CLinearTransitionFromSpeed::Create  
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
  
##  <a name="a-namemdblfinalvaluea--clineartransitionfromspeedmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed::m_dblFinalValue  
 El valor de la animación al final de la transición.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemdblspeeda--clineartransitionfromspeedmdblspeed"></a><a name="m_dblspeed"></a>CLinearTransitionFromSpeed::m_dblSpeed  
 El valor absoluto de la velocidad de la variable.  
  
```  
DOUBLE m_dblSpeed;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

