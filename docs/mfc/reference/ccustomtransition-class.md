---
title: Clase CCustomTransition | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
dev_langs: C++
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b94fd32bd00a484c5f8e3ba9e86efc5a9637e4e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccustomtransition-class"></a>Clase CCustomTransition
Implementa una transición personalizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Construye un objeto de transición personalizada.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Establece un valor inicial, que se aplicarán a una variable de animación asociada a esta transición.|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Establece una velocidad inicial, que se aplicarán a una variable de animación asociada a esta transición.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Especifica si se ha especificado el valor inicial con SetInitialValue.|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Especifica si se ha especificado el progreso inicial con SetInitialVelocity.|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|Almacena el valor inicial.|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Almacena el progreso inicial.|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Almacena un puntero a un interpolador personalizado.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CCustomTransitions permite a los desarrolladores implementar transiciones personalizadas. Se crea y utiliza como una transición estándar, pero su constructor acepta como parámetro un puntero a un interpolador personalizado. Realice los pasos siguientes para usar transiciones personalizadas: 1. Derive una clase de CCustomInterpolator e implemente al menos InterpolateValue método. 2. Asegúrese de que la duración del objeto personalizado interpolador debe tener más de duración de animación que se utiliza. 3. Instancias (mediante el operador new) de un objeto de CCustomTransition y pasar un puntero a un interpolador personalizado en el constructor. 4. Llamar a CCustomTransition::SetInitialValue y CCustomTransition::SetInitialVelocity si estos parámetros son necesarios para la interpolación personalizada. 5. Sitúe el puntero pase personalizado al método AddTransition del objeto de animación, cuyo valor debe animarse con el algoritmo personalizado. 6. Cuando tenga que cambiar el valor del objeto de animación API de animación de Windows llamará a InterpolateValue (y otros métodos relevantes) en CCustomInterpolator.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCustomTransition`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="ccustomtransition"></a>CCustomTransition::CCustomTransition  
 Construye un objeto de transición personalizada.  
  
```  
CCustomTransition(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parámetros  
 `pInterpolator`  
 Un puntero a interpolador personalizado.  
  
##  <a name="create"></a>CCustomTransition::Create  
 Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,  
    IUIAnimationTransitionFactory* pFactory);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFactory`  
 Un puntero al generador de transición, que es responsable de la creación de transiciones personalizadas.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Este método también puede establecer valor inicial y el progreso inicial que se aplicará a una variable de animación, que está asociada a esta transición. Para ello tendrá que llamar a SetInitialValue y SetInitialVelocity antes de que el marco de trabajo crea el objeto COM de transición encapsulado (se produce cuando se llama a CAnimationController::AnimateGroup).  
  
##  <a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified  
 Especifica si se ha especificado el valor inicial con SetInitialValue.  
  
```  
BOOL m_bInitialValueSpecified;  
```  
  
##  <a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified  
 Especifica si se ha especificado el progreso inicial con SetInitialVelocity.  
  
```  
BOOL m_bInitialVelocitySpecified;  
```  
  
##  <a name="m_initialvalue"></a>CCustomTransition::m_initialValue  
 Almacena el valor inicial.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity  
 Almacena el progreso inicial.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator  
 Almacena un puntero a un interpolador personalizado.  
  
```  
CCustomInterpolator* m_pInterpolator;  
```  
  
##  <a name="setinitialvalue"></a>CCustomTransition::SetInitialValue  
 Establece un valor inicial, que se aplicarán a una variable de animación asociada a esta transición.  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialValue`  
  
##  <a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity  
 Establece una velocidad inicial, que se aplicarán a una variable de animación asociada a esta transición.  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialVelocity`  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
