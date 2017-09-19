---
title: Clase CAnimationSize | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationSize class
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
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
ms.openlocfilehash: 84b9ae3b81f72f6c0ae8e88f78357c29e8d82ffd
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="canimationsize-class"></a>Clase CAnimationSize
Implementa la funcionalidad de un objeto cuyas dimensiones se pueden animar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](#canimationsize)|Sobrecargado. Construye un objeto de tamaño de la animación.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](#addtransition)|Agrega las transiciones de ancho y alto.|  
|[CAnimationSize::GetCX](#getcx)|Proporciona acceso a CAnimationVariable que representa el ancho.|  
|[CAnimationSize::GetCY](#getcy)|Proporciona acceso a CAnimationVariable que representa el alto.|  
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para Width y Height.|  
|[CAnimationSize::GetValue](#getvalue)|Devuelve el valor actual.|  
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](#operator_csize)|Convierte un CAnimationSize un CSize.|  
|[CAnimationSize::operator =](#operator_eq)|Asigna szSrc a CAnimationSize.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationSize::m_cxValue](#m_cxvalue)|La variable de animación encapsulado que representa el ancho del tamaño de la animación.|  
|[CAnimationSize::m_cyValue](#m_cyvalue)|La variable de animación encapsulado que representa el alto del tamaño de la animación.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationSize encapsula dos objetos CAnimationVariable y aplicaciones puede representar un tamaño. Por ejemplo, puede utilizar esta clase para animar un tamaño de dos objeto tridimensional en la pantalla (como en el rectángulo, controlar etcetera). Para utilizar esta clase en la aplicación, simplemente crear una instancia de un objeto de esta clase, agregue al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición se aplique a ancho o alto.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationSize` 
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationSize::AddTransition  
 Agrega las transiciones de ancho y alto.  
  
```  
void AddTransition(
    CBaseTransition* pCXTransition,  
    CBaseTransition* pCYTransition);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCXTransition`  
 Puntero a la transición para el ancho.  
  
 `pCYTransition`  
 Puntero a la transición de alto.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicará a las variables de animación para ancho y alto. Al agregar transiciones, no se aplican inmediatamente y almacenados en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no es necesario aplicar una transición a una de las dimensiones, puede pasar NULL.  
  
##  <a name="canimationsize"></a>CAnimationSize::CAnimationSize  
 Construye un objeto de tamaño de la animación.  
  
```  
CAnimationSize();

 
CAnimationSize(
    const CSize& szDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `szDefault`  
 Especifica el tamaño predeterminado.  
  
 `nGroupID`  
 Especifica el identificador de grupo.  
  
 `nObjectID`  
 Especifica el identificador de objeto.  
  
 `dwUserData`  
 Especifica los datos definidos por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Se construye el objeto con valores predeterminados para el ancho, alto, objeto de identificador y el identificador de grupo, que se establecerá en 0. Puede cambiar posteriormente en tiempo de ejecución mediante SetDefaultValue y SetID.  
  
##  <a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList  
 Coloca las variables de animación encapsulado en una lista.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parámetros  
 `lst`  
 Cuando la función vuelve, contiene punteros a dos objetos CAnimationVariable que representa el ancho y alto.  
  
##  <a name="getcx"></a>CAnimationSize::GetCX  
 Proporciona acceso a CAnimationVariable que representa el ancho.  
  
```  
CAnimationVariable& GetCX();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa el ancho.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa el ancho.  
  
##  <a name="getcy"></a>CAnimationSize::GetCY  
 Proporciona acceso a CAnimationVariable que representa el alto.  
  
```  
CAnimationVariable& GetCY();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a CAnimationVariable encapsulado que representa el alto.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa el alto.  
  
##  <a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue  
 Devuelve los valores predeterminados para Width y Height.  
  
```  
CSize GetDefaultValue();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto CSize que contiene los valores predeterminados.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor predeterminado, que se ha establecido previamente mediante el constructor o SetDefaultValue.  
  
##  <a name="getvalue"></a>CAnimationSize::GetValue  
 Devuelve el valor actual.  
  
```  
BOOL GetValue(CSize& szValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `szValue`  
 Salida. Cuando este método vuelve, contiene el valor actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si el valor actual se recuperó correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar el valor actual del tamaño de la animación. Si este método produce un error o no se hayan inicializado para el ancho y el tamaño de los objetos COM subyacentes, szValue contiene el valor predeterminado, que estableció anteriormente en el constructor o SetDefaultValue.  
  
##  <a name="m_cxvalue"></a>CAnimationSize::m_cxValue  
 La variable de animación encapsulado que representa el ancho del tamaño de la animación.  
  
```  
CAnimationVariable m_cxValue;  
```  
  
##  <a name="m_cyvalue"></a>CAnimationSize::m_cyValue  
 La variable de animación encapsulado que representa el alto del tamaño de la animación.  
  
```  
CAnimationVariable m_cyValue;  
```  
  
##  <a name="operator_csize"></a>CAnimationSize::operator CSize  
 Convierte un CAnimationSize un CSize.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del tamaño de la animación como CSize.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama internamente a GetValue. Si se produce un error en GetValue por alguna razón, el tamaño devuelto contendrá valores predeterminados para Width y Height.  
  
##  <a name="operator_eq"></a>CAnimationSize::operator =  
 Asigna szSrc a CAnimationSize.  
  
```  
void operator=(const CSize& szSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `szSrc`  
 Hace referencia a CSize o tamaño.  
  
### <a name="remarks"></a>Comentarios  
 Asigna szSrc a CAnimationSize. Se recomienda hacerlo antes del inicio de la animación, ya que llama a este operador SetDefaultValue, que vuelve a crear los objetos COM subyacentes para ancho y alto si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
##  <a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue  
 Establece el valor predeterminado.  
  
```  
void SetDefaultValue(const CSize& szDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `szDefault`  
 Especifica el nuevo tamaño de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este método asigna valores predeterminados para el ancho y alto del tamaño de la animación. También crea los objetos COM subyacentes si se han creado. Si está suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

