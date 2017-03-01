---
title: Clase CAnimationValue | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CAnimationValue
- CAnimationValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue class
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 083c8be9a0d9d518d5353b6d02c0050944312805
ms.lasthandoff: 02/24/2017

---
# <a name="canimationvalue-class"></a>Clase CAnimationValue
Implementa la funcionalidad del objeto de animación que tiene un valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationValue::CAnimationValue](#canimationvalue)|Sobrecargado. Construye un objeto CAnimationValue.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationValue::AddTransition](#addtransition)|Agrega una transición que se aplicará a un valor.|  
|[CAnimationValue::GetValue](#getvalue)|Sobrecargado. Recupera el valor actual.|  
|[CAnimationValue::GetVariable](#getvariable)|Proporciona acceso a la variable de animación encapsulado.|  
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Coloca la variable de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationValue::operator doble](#operator_double)|Proporciona la conversión entre CAnimationValue y DOUBLE.|  
|[INT32 CAnimationValue::operator](#operator_int32)|Proporciona la conversión entre CAnimationValue y INT32.|  
|[CAnimationValue::operator =](#operator_eq)|Sobrecargado. Asigna un valor INT32 a CAnimationValue.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationValue::m_value](#m_value)|La variable de animación encapsulado que representa el valor de la animación.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationValue encapsula un único objeto CAnimationVariable y aplicaciones puede representar un único valor animado. Por ejemplo, puede utilizar esta clase para transparencia animado (efecto de atenuación), ángulo (para girar objetos), o en cualquier otro caso, cuando necesite crear una animación depende de un único valor animado. Para utilizar esta clase en la aplicación, simplemente crear una instancia de un objeto de esta clase, agregue al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará el valor.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationValue`
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-nameaddtransitiona--canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition  
 Agrega una transición que se aplicará a un valor.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTransition`  
 Un puntero al objeto de transición.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar una transición a una lista interna de transiciones que se aplicará a una variable de animación. Al agregar transiciones, no se aplican inmediatamente y almacenados en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup.  
  
##  <a name="a-namecanimationvaluea--canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue  
 Construye un objeto CAnimationValue.  
  
```  
CAnimationValue();

 
CAnimationValue(
    DOUBLE dblDefaultValue,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblDefaultValue`  
 Especifica el valor predeterminado.  
  
 `nGroupID`  
 Especifica el identificador de grupo.  
  
 `nObjectID`  
 Especifica el identificador de objeto.  
  
 `dwUserData`  
 Especifica los datos definidos por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Construye el objeto CAnimationValue con propiedades predeterminadas: valor predeterminado, Id. de grupo y el Id. de objeto se establecen en 0.  
  
##  <a name="a-namegetanimationvariablelista--canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList  
 Coloca la variable de animación encapsulado en una lista.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parámetros  
 `lst`  
 Cuando la función devuelve, contiene un puntero a CAnimationVariable que representa el valor animado.  
  
##  <a name="a-namegetvaluea--canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::GetValue  
 Recupera el valor actual.  
  
```  
BOOL GetValue(DOUBLE& dblValue);  
BOOL GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblValue`  
 Salida. Cuando se devuelve la función contiene un valor actual de la animación.  
  
 `nValue`  
 Salida. Cuando se devuelve la función contiene un valor actual de la animación.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el valor actual se recuperó correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor actual. Esta implementación llama al objeto COM encapsulado y, si se produce un error en la llamada, este método devuelve el valor predeterminado que se configuró anteriormente en el constructor o con SetDefaultValue.  
  
##  <a name="a-namegetvariablea--canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::GetVariable  
 Proporciona acceso a la variable de animación encapsulado.  
  
```  
CAnimationVariable& GetVariable();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la variable de animación encapsulado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para tener acceso a la variable de animación encapsulado. Desde CAnimationVariable obtener acceso al objeto subyacente de IUIAnimationVariable, cuyo puntero puede ser NULL si no se ha creado la animación.  
  
##  <a name="a-namemvaluea--canimationvaluemvalue"></a><a name="m_value"></a>CAnimationValue::m_value  
 La variable de animación encapsulado que representa el valor de la animación.  
  
```  
CAnimationVariable m_value;  
```  
  
##  <a name="a-nameoperatordoublea--canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::operator doble  
 Proporciona la conversión entre CAnimationValue y DOUBLE.  
  
```  
operator DOUBLE();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual de animación.  
  
### <a name="remarks"></a>Comentarios  
 Proporciona la conversión entre CAnimationValue y DOUBLE. Internamente, este método llama GetValue y no comprueba si hay errores. Si se produce un error en GetValue, el valor devuelto contendrá un valor predeterminado establecido previamente en el constructor o con SetDefaultValue.  
  
##  <a name="a-nameoperatorint32a--canimationvalueoperator-int32"></a><a name="operator_int32"></a>INT32 CAnimationValue::operator  
 Proporciona la conversión entre CAnimationValue y INT32.  
  
```  
operator INT32();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual de animación como entero.  
  
### <a name="remarks"></a>Comentarios  
 Proporciona la conversión entre CAnimationValue y INT32. Internamente, este método llama GetValue y no comprueba si hay errores. Si se produce un error en GetValue, el valor devuelto contendrá un valor predeterminado establecido previamente en el constructor o con SetDefaultValue.  
  
##  <a name="a-nameoperatoreqa--canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::operator =  
 Asigna un valor doble a CAnimationValue.  
  
```  
void operator=(DOUBLE dblVal);  
void operator=(INT32 nVal);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblVal`  
 Especifica el valor que se asigna al valor de animación.  
  
 `nVal`  
 Especifica el valor que se asigna al valor de animación.  
  
### <a name="remarks"></a>Comentarios  
 Asigna un valor doble a CAnimationValue. Este valor se establece como un valor predeterminado para la variable de animación encapsulado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
##  <a name="a-namesetdefaultvaluea--canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue  
 Establece el valor predeterminado.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblDefaultValue`  
 Especifica el valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer un valor predeterminado. Cuando la animación no se inició o no se creó el objeto COM subyacente, se devuelve un valor predeterminado para la aplicación. Si ya se creó el objeto COM subyacente encapsulado en CAnimationVarible, este método vuelve a crear, por lo tanto, debe volver a llamar a métodos EnableValueChanged/EnableIntegerValueChanged.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

