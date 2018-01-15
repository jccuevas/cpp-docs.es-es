---
title: Clase CAnimationPoint | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ab685c223c4a86c35ba0feb578d93f58844734b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="canimationpoint-class"></a>Clase CAnimationPoint
Implementa la funcionalidad de un punto cuyas coordenadas se pueden animar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationPoint : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Sobrecargado. Construye el objeto CAnimationPoint.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::AddTransition](#addtransition)|Agrega las transiciones de X y coordenadas.|  
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para X coordenadas e Y.|  
|[CAnimationPoint::GetValue](#getvalue)|Devuelve el valor actual.|  
|[CAnimationPoint::GetX](#getx)|Proporciona acceso a CAnimationVariable para la coordenada X.|  
|[CAnimationPoint::GetY](#gety)|Proporciona acceso a CAnimationVariable de coordenada Y.|  
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Convierte un CAnimationPoint CPoint.|  
|[CAnimationPoint::operator =](#operator_eq)|Asigna ptSrc a CAnimationPoint.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::m_xValue](#m_xvalue)|La variable de animación encapsulado que representa X coordenadas del punto de la animación.|  
|[CAnimationPoint::m_yValue](#m_yvalue)|La variable de animación encapsulado que representa la coordenada Y del punto de la animación.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationPoint encapsula los dos objetos CAnimationVariable y aplicaciones puede representar un punto. Por ejemplo, puede usar esta clase para animar una posición de cualquier objeto en la pantalla (como cadena de texto, círculo, punto etcetera). Para utilizar esta clase en la aplicación, simplemente cree instancias de un objeto de esta clase, agregarlo al controlador de animación con CAnimationController::AddAnimationObject y llame a AddTransition para cada transición se aplique a las coordenadas X o Y.  
  
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
 Puntero a la transición de coordenadas X.  
  
 `pYTransition`  
 Puntero a la transición para Y coordinar.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicará a las variables de la animación para X coordenadas e Y. Al agregar transiciones, no se aplican de forma inmediata y almacenados en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no es necesario aplicar una transición a uno de coordenadas, puede pasar NULL.  
  
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
 Especifica las coordenadas de punto de forma predeterminada.  
  
 `nGroupID`  
 Especifica el identificador de grupo.  
  
 `nObjectID`  
 Especifica el identificador de objeto.  
  
 `dwUserData`  
 Especifica los datos definidos por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Construye el objeto CAnimationPoint con propiedades predeterminadas: predeterminado coordenadas del punto, Id. de grupo y el Id. de objeto se establecen en 0.  
  
##  <a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList  
 Coloca las variables de animación encapsulado en una lista.  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parámetros  
 `lst`  
 Cuando la función devuelve, contiene punteros a dos objetos CAnimationVariable que representa las coordenadas X e Y.  
  
##  <a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue  
 Devuelve los valores predeterminados para X coordenadas e Y.  
  
```  
CPoint GetDefaultValue();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de punto de contenedor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor predeterminado, que se ha establecido anteriormente al constructor o SetDefaultValue.  
  
##  <a name="getvalue"></a>CAnimationPoint::GetValue  
 Devuelve el valor actual.  
  
```  
BOOL GetValue(CPoint& ptValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptValue`  
 Salida. Cuando este método vuelve, contiene el valor actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si el valor actual se ha recuperado correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor actual del punto de la animación. Si este método produce un error o COM subyacente de objetos para X y coordenadas Y no se hayan inicializado, ptValue contiene el valor predeterminado, que anteriormente se estableció en el constructor o SetDefaultValue.  
  
##  <a name="getx"></a>CAnimationPoint::GetX  
 Proporciona acceso a CAnimationVariable para la coordenada X.  
  
```  
CAnimationVariable& GetX();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa X coordinar.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa X coordinar.  
  
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
 La variable de animación encapsulado que representa X coordenadas del punto de la animación.  
  
```  
CAnimationVariable m_xValue;  
```  
  
##  <a name="m_yvalue"></a>CAnimationPoint::m_yValue  
 La variable de animación encapsulado que representa la coordenada Y del punto de la animación.  
  
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
 Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el punto devuelto contendrá los valores predeterminados para X coordenadas e Y.  
  
##  <a name="operator_eq"></a>CAnimationPoint::operator =  
 Asigna ptSrc a CAnimationPoint.  
  
```  
void operator=(const CPoint& ptSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptSrc`  
 Hace referencia a CPoint o punto.  
  
### <a name="remarks"></a>Comentarios  
 Asigna ptSrc a CAnimationPoint. Se recomienda hacer que antes del inicio de la animación, dado que este operador llama SetDefaultValue, que vuelve a crear el modelo COM subyacente objetos de coordenadas X e Y si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
##  <a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue  
 Establece el valor predeterminado.  
  
```  
void SetDefaultValue(const POINT& ptDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptDefault`  
 Especifica el valor de punto de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este valor de predeterminado de métodos asigna valores a las coordenadas X e Y del punto de la animación. También crea los objetos COM subyacentes si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
