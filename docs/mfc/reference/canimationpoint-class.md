---
title: Clase CAnimationPoint | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationPoint class
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
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
ms.openlocfilehash: a6a59ad85928c199a8dd911b915076ffbd0b0e37
ms.lasthandoff: 02/24/2017

---
# <a name="canimationpoint-class"></a>Clase CAnimationPoint
Implementa la funcionalidad de un punto cuyas coordenadas se pueden animar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationPoint : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Sobrecargado. Construye el objeto CAnimationPoint.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::AddTransition](#addtransition)|Agrega las transiciones de X y coordenadas.|  
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para X y coordenadas.|  
|[CAnimationPoint::GetValue](#getvalue)|Devuelve el valor actual.|  
|[CAnimationPoint::GetX](#getx)|Proporciona acceso a CAnimationVariable para la coordenada X.|  
|[CAnimationPoint::GetY](#gety)|Proporciona acceso a CAnimationVariable de coordenada Y.|  
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Convierte un CAnimationPoint CPoint.|  
|[CAnimationPoint::operator =](#operator_eq)|Asigna ptSrc a CAnimationPoint.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::m_xValue](#m_xvalue)|La variable de animación encapsulado que representa la X coordenadas de punto de animación.|  
|[CAnimationPoint::m_yValue](#m_yvalue)|La variable de animación encapsulado que representa la coordenada Y del punto de animación.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationPoint encapsula dos objetos CAnimationVariable y aplicaciones puede representar un punto. Por ejemplo, puede utilizar esta clase para animar una posición de cualquier objeto en la pantalla (como cadena de texto, círculo, punto etcetera). Para utilizar esta clase en la aplicación, simplemente crear una instancia de un objeto de esta clase, agregue al controlador de animación mediante CAnimationController::AddAnimationObject y llamar a AddTransition para cada transición se aplique a las coordenadas X o Y.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationPoint`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationPoint::AddTransition  
 Agrega las transiciones de X y coordenadas.  
  
```  
void AddTransition(
    CBaseTransition* pXTransition,  
    CBaseTransition* pYTransition);
```  
  
### <a name="parameters"></a>Parámetros  
 `pXTransition`  
 Puntero a la transición de las coordenadas X.  
  
 `pYTransition`  
 Un puntero a la transición y coordinar.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicará a las variables de animación para X y coordenadas. Al agregar transiciones, no se aplican inmediatamente y almacenados en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no es necesario aplicar una transición a una de coordenadas, puede pasar NULL.  
  
##  <a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint  
 Construye el objeto CAnimationPoint.  
  
```  
CAnimationPoint();

 
CAnimationPoint(
    const CPoint& ptDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptDefault`  
 Especifica las coordenadas del punto de forma predeterminada.  
  
 `nGroupID`  
 Especifica el identificador de grupo.  
  
 `nObjectID`  
 Especifica el identificador de objeto.  
  
 `dwUserData`  
 Especifica los datos definidos por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Construye el objeto CAnimationPoint con propiedades predeterminadas: coordenadas del punto como valor predeterminado, el Id. de grupo y el Id. de objeto se establecen en 0.  
  
##  <a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList  
 Coloca las variables de animación encapsulado en una lista.  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parámetros  
 `lst`  
 Cuando la función vuelve, contiene punteros a dos objetos CAnimationVariable que representa las coordenadas X e Y.  
  
##  <a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue  
 Devuelve los valores predeterminados para X y coordenadas.  
  
```  
CPoint GetDefaultValue();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de punto de contenedor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor predeterminado, que se ha establecido previamente mediante el constructor o SetDefaultValue.  
  
##  <a name="getvalue"></a>CAnimationPoint::GetValue  
 Devuelve el valor actual.  
  
```  
BOOL GetValue(CPoint& ptValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptValue`  
 Salida. Cuando este método vuelve, contiene el valor actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si el valor actual se recuperó correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor actual del punto de animación. Si este método produce un error o COM subyacente de objetos para X y no se han inicializado coordenadas, ptValue contiene el valor predeterminado, que estableció anteriormente en el constructor o SetDefaultValue.  
  
##  <a name="getx"></a>CAnimationPoint::GetX  
 Proporciona acceso a CAnimationVariable para la coordenada X.  
  
```  
CAnimationVariable& GetX();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa la X de coordenadas.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la X de coordenadas.  
  
##  <a name="gety"></a>CAnimationPoint::GetY  
 Proporciona acceso a CAnimationVariable de coordenada Y.  
  
```  
CAnimationVariable& GetY();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa la coordenada Y.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada Y.  
  
##  <a name="m_xvalue"></a>CAnimationPoint::m_xValue  
 La variable de animación encapsulado que representa la X coordenadas de punto de animación.  
  
```  
CAnimationVariable m_xValue;  
```  
  
##  <a name="m_yvalue"></a>CAnimationPoint::m_yValue  
 La variable de animación encapsulado que representa la coordenada Y del punto de animación.  
  
```  
CAnimationVariable m_yValue;  
```  
  
##  <a name="operator_cpoint"></a>CAnimationPoint::operator CPoint  
 Convierte un CAnimationPoint CPoint.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual de CAnimationPoint como CPoint.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama internamente a GetValue. Si se produce un error en GetValue por alguna razón, el punto devuelto contendrá valores predeterminados para X y coordenadas.  
  
##  <a name="operator_eq"></a>CAnimationPoint::operator =  
 Asigna ptSrc a CAnimationPoint.  
  
```  
void operator=(const CPoint& ptSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptSrc`  
 Hace referencia a CPoint o punto.  
  
### <a name="remarks"></a>Comentarios  
 Asigna ptSrc a CAnimationPoint. Se recomienda hacer que antes del inicio de la animación, ya que llama a este operador SetDefaultValue, que vuelve a crear el COM subyacente objetos de coordenadas X e Y si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
##  <a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue  
 Establece el valor predeterminado.  
  
```  
void SetDefaultValue(const POINT& ptDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptDefault`  
 Especifica el valor de punto de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este valor predeterminado asigna de métodos los valores en las coordenadas X e Y de punto de animación. También crea los objetos COM subyacentes si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

