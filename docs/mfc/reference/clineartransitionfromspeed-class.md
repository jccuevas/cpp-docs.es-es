---
title: Clase CLinearTransitionFromSpeed | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64c8829336378e24759bc26e306fb7b43ab226bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="clineartransitionfromspeed-class"></a>Clase CLinearTransitionFromSpeed
Encapsula una transición de velocidad lineal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Construye un objeto de la transición de velocidad lineal y la inicializa con la velocidad y el valor final.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|  
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|El valor absoluto del progreso de la variable.|  
  
## <a name="remarks"></a>Comentarios  
 Durante una transición de velocidad lineal, cambia el valor de la variable de animación a una velocidad especificada. La duración de la transición viene determinada por la diferencia entre el valor inicial y el valor final especificado. Debido a que todas las transiciones se desactivan automáticamente, se recomienda asignada a ellos con el operador de nuevo. Se crea el objeto de IUIAnimationTransition COM encapsulado por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="clineartransitionfromspeed"></a>  CLinearTransitionFromSpeed::CLinearTransitionFromSpeed  
 Construye un objeto de la transición de velocidad lineal y la inicializa con la velocidad y el valor final.  
  
```  
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblSpeed`  
 El valor absoluto del progreso de la variable.  
  
 `dblFinalValue`  
 El valor de la variable de animación al final de la transición.  
  
##  <a name="create"></a>  CLinearTransitionFromSpeed::Create  
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
  
##  <a name="m_dblfinalvalue"></a>  CLinearTransitionFromSpeed::m_dblFinalValue  
 El valor de la variable de animación al final de la transición.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblspeed"></a>  CLinearTransitionFromSpeed::m_dblSpeed  
 El valor absoluto del progreso de la variable.  
  
```  
DOUBLE m_dblSpeed;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
