---
title: Clase CAnimationRect | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationRect class
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: f935884301030166572e356fffe88439f843f2c7
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="canimationrect-class"></a>Clase CAnimationRect
Implementa la funcionalidad de un rectángulo cuyos lados se pueden animar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationRect::CAnimationRect](#canimationrect)|Sobrecargado. Construye un objeto rect de animación.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationRect::AddTransition](#addtransition)|Agrega transiciones de las coordenadas izquierda, superior, derecho e inferior.|  
|[CAnimationRect::GetBottom](#getbottom)|Proporciona acceso a CAnimationVariable que representa la coordenada inferior.|  
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para los límites del rectángulo.|  
|[CAnimationRect::GetLeft](#getleft)|Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.|  
|[CAnimationRect::GetRight](#getright)|Proporciona acceso a CAnimationVariable que representa la coordenada derecha.|  
|[CAnimationRect::GetTop](#gettop)|Proporciona acceso a CAnimationVariable que representa la coordenada superior.|  
|[CAnimationRect::GetValue](#getvalue)|Devuelve el valor actual.|  
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationRect::operator RECT](#operator_rect)|Convierte un CAnimationRect en un elemento Rect.|  
|[CAnimationRect::operator =](#operator_eq)|Rect se asigna a CAnimationRect.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Especifica si el rectángulo ha de tamaño fijo.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Enlaza la variable de animación encapsulado que representa la parte inferior del rectángulo de animación.|  
|[CAnimationRect::m_leftValue](#m_leftvalue)|Enlaza la variable de animación encapsulado que representa la izquierda del rectángulo de animación.|  
|[CAnimationRect::m_rightValue](#m_rightvalue)|Enlaza la variable de animación encapsulado que representa el derecho del rectángulo de animación.|  
|[CAnimationRect::m_szInitial](#m_szinitial)|Especifica el tamaño inicial del rectángulo de animación.|  
|[CAnimationRect::m_topValue](#m_topvalue)|Enlaza la variable de animación encapsulado que representa la parte superior del rectángulo de animación.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationRect encapsula cuatro objetos CAnimationVariable y puede representar en aplicaciones de un rectángulo. Para utilizar esta clase en la aplicación, simplemente crear una instancia de un objeto de esta clase, agregue al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará a la izquierda, derecha coordenadas superior e inferior.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationRect`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationRect::AddTransition  
 Agrega transiciones de las coordenadas izquierda, superior, derecho e inferior.  
  
```  
void AddTransition(
    CBaseTransition* pLeftTransition,  
    CBaseTransition* pTopTransition,  
    CBaseTransition* pRightTransition,  
    CBaseTransition* pBottomTransition);
```  
  
### <a name="parameters"></a>Parámetros  
 `pLeftTransition`  
 Especifica la transición de la izquierda.  
  
 `pTopTransition`  
 Especifica la transición de la parte superior.  
  
 `pRightTransition`  
 Especifica la transición para el lado derecho.  
  
 `pBottomTransition`  
 Especifica la transición para el lado inferior.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicará a las variables de la animación de los lados del rectángulo. Al agregar transiciones, no se aplican inmediatamente y almacenados en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no es necesario aplicar una transición a uno de los lados del rectángulo, se puede pasar NULL.  
  
##  <a name="canimationrect"></a>CAnimationRect::CAnimationRect  
 Construye un objeto CAnimationRect.  
  
```  
CAnimationRect();

 
CAnimationRect(
    const CRect& rect,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    const CPoint& pt,  
    const CSize& sz,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    int nLeft,  
    int nTop,  
    int nRight,  
    int nBottom,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Especifica el rectángulo predeterminado.  
  
 `nGroupID`  
 Especifica el identificador de grupo.  
  
 `nObjectID`  
 Especifica el identificador de objeto.  
  
 `dwUserData`  
 Especifica los datos definidos por el usuario.  
  
 `pt`  
 Coordenada de la esquina superior izquierda.  
  
 `sz`  
 Tamaño del rectángulo.  
  
 `nLeft`  
 Especifica la coordenada del límite izquierdo.  
  
 `nTop`  
 Especifica la coordenada del límite superior.  
  
 `nRight`  
 Especifica la coordenada del límite derecho.  
  
 `nBottom`  
 Especifica la coordenada del límite inferior.  
  
### <a name="remarks"></a>Comentarios  
 Se construye el objeto con valores predeterminados para la izquierda, superior, derecho e inferior, Id. de objeto y el identificador de grupo, que se establecerá en 0. Puede cambiar posteriormente en tiempo de ejecución mediante SetDefaultValue y SetID.  
  
##  <a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList  
 Coloca las variables de animación encapsulado en una lista.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parámetros  
 `lst`  
 Cuando la función vuelve, contiene punteros a cuatro objetos CAnimationVariable que representa las coordenadas del rectángulo.  
  
##  <a name="getbottom"></a>CAnimationRect::GetBottom  
 Proporciona acceso a CAnimationVariable que representa la coordenada inferior.  
  
```  
CAnimationVariable& GetBottom();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa la coordenada inferior.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada de la parte inferior.  
  
##  <a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue  
 Devuelve los valores predeterminados para los límites del rectángulo.  
  
```  
CRect GetDefaultValue();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de CRect que contiene los valores predeterminados para la izquierda, derecha, superior e inferior.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor predeterminado, que se ha establecido previamente mediante el constructor o SetDefaultValue.  
  
##  <a name="getleft"></a>CAnimationRect::GetLeft  
 Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.  
  
```  
CAnimationVariable& GetLeft();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa la coordenada izquierda.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada izquierda.  
  
##  <a name="getright"></a>CAnimationRect::GetRight  
 Proporciona acceso a CAnimationVariable que representa la coordenada derecha.  
  
```  
CAnimationVariable& GetRight();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa la coordenada derecha.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada derecha.  
  
##  <a name="gettop"></a>CAnimationRect::GetTop  
 Proporciona acceso a CAnimationVariable que representa la coordenada superior.  
  
```  
CAnimationVariable& GetTop();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa la coordenada superior.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada superior.  
  
##  <a name="getvalue"></a>CAnimationRect::GetValue  
 Devuelve el valor actual.  
  
```  
BOOL GetValue(CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Salida. Cuando este método vuelve, contiene el valor actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si el valor actual se recuperó correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor actual del rectángulo de animación. Si este método produce un error o COM subyacente de objetos para izquierda, superior, derecho e inferior no se ha inicializado, rect contiene el valor predeterminado, que estableció anteriormente en el constructor o SetDefaultValue.  
  
##  <a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize  
 Especifica si el rectángulo ha de tamaño fijo.  
  
```  
BOOL m_bFixedSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si este miembro es true, el tamaño del rectángulo es fijo y derecha y valores inferiores se vuelven a calcular cada vez que se mueve la esquina superior izquierda según el tamaño fijo. Establezca este valor en TRUE para mover fácilmente el rectángulo alrededor de la pantalla. En este caso se omiten las transiciones aplicadas a las coordenadas de derecho e inferior. El tamaño se almacena internamente cuando construya el objeto y llamar a SetDefaultValue. De forma predeterminada, este miembro se establece en FALSE.  
  
##  <a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue  
 Enlaza la variable de animación encapsulado que representa la parte inferior del rectángulo de animación.  
  
```  
CAnimationVariable m_bottomValue;  
```  
  
##  <a name="m_leftvalue"></a>CAnimationRect::m_leftValue  
 Enlaza la variable de animación encapsulado que representa la izquierda del rectángulo de animación.  
  
```  
CAnimationVariable m_leftValue;  
```  
  
##  <a name="m_rightvalue"></a>CAnimationRect::m_rightValue  
 Enlaza la variable de animación encapsulado que representa el derecho del rectángulo de animación.  
  
```  
CAnimationVariable m_rightValue;  
```  
  
##  <a name="m_szinitial"></a>CAnimationRect::m_szInitial  
 Especifica el tamaño inicial del rectángulo de animación.  
  
```  
CSize m_szInitial;  
```  
  
##  <a name="m_topvalue"></a>CAnimationRect::m_topValue  
 Enlaza la variable de animación encapsulado que representa la parte superior del rectángulo de animación.  
  
```  
CAnimationVariable m_topValue;  
```  
  
##  <a name="operator_rect"></a>CAnimationRect::operator RECT  
 Convierte un CAnimationRect en un elemento Rect.  
  
```  
operator RECT();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del rectángulo de animación como objeto Rect.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama internamente a GetValue. Si se produce un error en GetValue por alguna razón, el rectángulo devuelto contendrá valores predeterminados para todas las coordenadas de rectángulo.  
  
##  <a name="operator_eq"></a>CAnimationRect::operator =  
 Rect se asigna a CAnimationRect.  
  
```  
void operator=(const RECT& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 El nuevo valor del rectángulo de animación.  
  
### <a name="remarks"></a>Comentarios  
 Se recomienda hacerlo antes del inicio de la animación, ya que llama a este operador SetDefaultValue, que vuelve a crear los objetos COM subyacentes para los componentes de color si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
##  <a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue  
 Establece el valor predeterminado.  
  
```  
void SetDefaultValue(const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Especifica los nuevos valores predeterminados para la izquierda, superior, derecho e inferior.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este método asigna valores predeterminados a los límites del rectángulo. También crea los objetos COM subyacentes si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

