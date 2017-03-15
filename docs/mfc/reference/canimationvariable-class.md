---
title: Clase CAnimationVariable | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariable
- afxanimationcontroller/CAnimationVariable
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariable class
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
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
ms.openlocfilehash: 42513c841f6dc891369d7d6640ced1aa37f90e8e
ms.lasthandoff: 02/24/2017

---
# <a name="canimationvariable-class"></a>Clase CAnimationVariable
Representa una variable de animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationVariable;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Construye un objeto de variable de animación.|  
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|Destructor. Se llama cuando se destruye un objeto CAnimationVariable.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::AddTransition](#addtransition)|Agrega una transición.|  
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Agrega las transiciones de la lista interna en guiones gráficos.|  
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Borra las transiciones.|  
|[CAnimationVariable::Create](#create)|Crea el objeto subyacente de COM de variable de animación.|  
|[CAnimationVariable::CreateTransitions](#createtransitions)|Crea todas las transiciones que se aplicará a esta variable de animación.|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Habilita o deshabilita el evento IntegerValueChanged.|  
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Habilita o deshabilita el evento ValueChanged.|  
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Devuelve el valor predeterminado.|  
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Devuelve el principal objeto de animación.|  
|[CAnimationVariable::GetValue](#getvalue)|Sobrecargado. Devuelve el valor actual de la animación.|  
|[CAnimationVariable::GetVariable](#getvariable)|Devuelve un puntero al objeto COM IUIAnimationVariable.|  
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado y libera el objeto COM IUIAnimationVariable.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Establece la relación entre una variable de animación y un objeto de animación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Especifica si se deben eliminar los objetos relacionados.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.|  
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Contiene una lista de las transiciones que animar esta variable de animación.|  
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Puntero a un objeto de animación que encapsula esta variable de animación.|  
|[CAnimationVariable::m_variable](#m_variable)|Almacena un puntero al objeto COM IUIAnimationVariable. NULL si aún no ha creado el objeto COM, o si no se pudo crear.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationVariable encapsula el objeto COM IUIAnimationVariable. También contiene una lista de las transiciones que se aplicará a la variable de animación en un guión gráfico. Objetos CAnimationVariable se incrustan en los objetos de animación, que se pueden representar en una aplicación de un valor animado, punto, tamaño, color y rectángulo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CAnimationVariable`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-namedtorcanimationvariablea--canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable  
 Destructor. Se llama cuando se destruye un objeto CAnimationVariable.  
  
```  
virtual ~CAnimationVariable();
```  
  
##  <a name="a-nameaddtransitiona--canimationvariableaddtransition"></a><a name="addtransition"></a>CAnimationVariable::AddTransition  
 Agrega una transición.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTransition`  
 Puntero a una transición a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método para agregar una transición a la lista interna de transiciones que se aplicará a la variable de animación. Esta lista debe borrarse cuando se ha programado una animación.  
  
##  <a name="a-nameapplytransitionsa--canimationvariableapplytransitions"></a><a name="applytransitions"></a>CAnimationVariable::ApplyTransitions  
 Agrega las transiciones de la lista interna en guiones gráficos.  
  
```  
void ApplyTransitions(
    CAnimationController* pController,  
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parámetros  
 `pController`  
 Puntero al controlador de animación principal.  
  
 `pStoryboard`  
 Puntero al guión gráfico.  
  
 `bDependOnKeyframes`  
 TRUE si este método debería agregar transiciones que dependen de los fotogramas clave.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega transiciones de la lista interna en guiones gráficos. Se llama desde el código de nivel superior varias veces para agregar transiciones que no dependen de los fotogramas clave y agregar transiciones que dependen de los fotogramas clave. Si no se ha creado la variable de animación objeto COM subyacente, este método crea en esta etapa.  
  
##  <a name="a-namecanimationvariablea--canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable  
 Construye un objeto de variable de animación.  
  
```  
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblDefaultValue`  
 Especifica el valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Construye un objeto de variable de animación y establece su valor predeterminado. Un valor predeterminado se utiliza cuando una variable no se anima o no se pueden animar.  
  
##  <a name="a-namecleartransitionsa--canimationvariablecleartransitions"></a><a name="cleartransitions"></a>CAnimationVariable::ClearTransitions  
 Borra las transiciones.  
  
```  
void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAutodestroy`  
 Especifica si este método debe eliminar objetos de la transición.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita todas las transiciones de la lista interna de las transiciones. Si bAutodestroy es TRUE, o m_bAutodestroyTransitions es TRUE, se eliminan las transiciones. De lo contrario, el llamador debe desasignar los objetos de la transición.  
  
##  <a name="a-namecreatea--canimationvariablecreate"></a><a name="create"></a>CAnimationVariable::Create  
 Crea el objeto subyacente de COM de variable de animación.  
  
```  
virtual BOOL Create(IUIAnimationManager* pManager);
```  
  
### <a name="parameters"></a>Parámetros  
 `pManager`  
 Un puntero al administrador de animación.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la variable de animación se creó correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea la variable de animación objeto COM subyacente y establece su valor predeterminado.  
  
##  <a name="a-namecreatetransitionsa--canimationvariablecreatetransitions"></a><a name="createtransitions"></a>CAnimationVariable::CreateTransitions  
 Crea todas las transiciones que se aplicará a esta variable de animación.  
  
```  
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
`pLibrary`  
 Un puntero a un [IUIAnimationTransitionLibrary interfaz](https://msdn.microsoft.com/library/windows/desktop/dd371897), que define una biblioteca de transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si las transiciones se crearon correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando es necesario crear las transiciones que se han agregado a la lista interna de la variable de transiciones.  
  
##  <a name="a-nameenableintegervaluechangedeventa--canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent  
 Habilita o deshabilita el evento IntegerValueChanged.  
  
```  
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 `pController`  
 Un puntero al controlador principal.  
  
 `bEnable`  
 TRUE: Habilitar eventos, FALSE - deshabilitar eventos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita el evento ValueChanged, el marco llama el método virtual CAnimationController::OnAnimationIntegerValueChanged. Debe invalidar en una clase derivada de CAnimationController para procesar este evento. Este método se llama cada vez que cambia el valor del entero de animación.  
  
##  <a name="a-nameenablevaluechangedeventa--canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent  
 Habilita o deshabilita el evento ValueChanged.  
  
```  
void EnableValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 `pController`  
 Un puntero al controlador principal.  
  
 `bEnable`  
 TRUE: Habilitar eventos, FALSE - deshabilitar eventos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita el evento ValueChanged, el marco llama el método virtual CAnimationController::OnAnimationValueChanged. Debe invalidar en una clase derivada de CAnimationController para procesar este evento. Este método se llama cada vez que cambia el valor de animación.  
  
##  <a name="a-namegetdefaultvaluea--canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue  
 Devuelve el valor predeterminado.  
  
```  
DOUBLE GetDefaultValue() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para obtener el valor predeterminado de animación. El valor predeterminado se puede establecer en el constructor o método SetDefaultValue.  
  
##  <a name="a-namegetparentanimationobjecta--canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject  
 Devuelve el principal objeto de animación.  
  
```  
CAnimationBaseObject* GetParentAnimationObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de animación principal, si se ha establecido una relación, de lo contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para recuperar un puntero a un objeto de animación primario (contenedor).  
  
##  <a name="a-namegetvaluea--canimationvariablegetvalue"></a><a name="getvalue"></a>CAnimationVariable::GetValue  
 Devuelve el valor actual de la animación.  
  
```  
HRESULT GetValue(DOUBLE& dblValue);  
HRESULT GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblValue`  
 El valor actual de la animación.  
  
 `nValue`  
 El valor actual de la animación.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el valor se obtuvo correctamente o no se ha creado la variable de animación subyacente. Código de error HRESULT en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método para recuperar el valor actual de la animación. Si no se ha creado el objeto COM subyacente, dblValue contendrá un valor predeterminado, cuando se devuelve la función.  
  
##  <a name="a-namegetvariablea--canimationvariablegetvariable"></a><a name="getvariable"></a>CAnimationVariable::GetVariable  
 Devuelve un puntero al objeto COM IUIAnimationVariable.  
  
```  
IUIAnimationVariable* GetVariable();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido al objeto COM IUIAnimationVariable, o NULL si la animación no se ha creado o no se puede crear.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para obtener acceso al objeto COM IUIAnimationVariable subyacente y llamar a sus métodos directamente si es necesario.  
  
##  <a name="a-namembautodestroytransitionsa--canimationvariablembautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions  
 Especifica si se deben eliminar los objetos relacionados.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer este valor en True para forzar la eliminación de objetos de transición cuando se eliminan de la lista de transiciones interna. Si este valor es FALSE, las transiciones deben eliminarse mediante una llamada a la aplicación. La lista de transiciones siempre se borra después de que se ha programado una animación. El valor predeterminado es FALSE.  
  
##  <a name="a-namemdbldefaultvaluea--canimationvariablemdbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue  
 Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.  
  
```  
DOUBLE m_dblDefaultValue;  
```  
  
##  <a name="a-namemlsttransitionsa--canimationvariablemlsttransitions"></a><a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions  
 Contiene una lista de las transiciones que animar esta variable de animación.  
  
```  
CObList m_lstTransitions;  
```  
  
##  <a name="a-namempparentobjecta--canimationvariablempparentobject"></a><a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject  
 Puntero a un objeto de animación que encapsula esta variable de animación.  
  
```  
CAnimationBaseObject* m_pParentObject;  
```  
  
##  <a name="a-namemvariablea--canimationvariablemvariable"></a><a name="m_variable"></a>CAnimationVariable::m_variable  
 Almacena un puntero al objeto COM IUIAnimationVariable. NULL si aún no ha creado el objeto COM, o si no se pudo crear.  
  
```  
ATL::CComPtr<IUIAnimationVariable> m_variable;  
```  
  
##  <a name="a-namesetdefaultvaluea--canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue  
 Establece el valor predeterminado y libera el objeto COM IUIAnimationVariable.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `dblDefaultValue`  
 Especifica el nuevo valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para restablecer el valor predeterminado. Este método libera el objeto COM IUIAnimationVariable interno, por lo tanto, cuando se vuelve a crear la variable de animación, el objeto COM subyacente obtiene el nuevo valor predeterminado. El valor predeterminado es devuelto por GetValue si no se crea el objeto COM que representa la variable de animación, o si la variable no se ha animado.  
  
##  <a name="a-namesetparentanimationobjecta--canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject  
 Establece la relación entre una variable de animación y un objeto de animación.  
  
```  
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentObject`  
 Puntero a un objeto de animación que contiene esta variable.  
  
### <a name="remarks"></a>Comentarios  
 Se llama internamente a este método para establecer una relación uno a uno entre una variable de animación y un objeto de animación que encapsula.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

