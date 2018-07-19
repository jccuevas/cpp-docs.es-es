---
title: Clase CAnimationVariable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 207adbba4635b80ba7b60af53f920b1af376e93d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957304"
---
# <a name="canimationvariable-class"></a>Clase CAnimationVariable
Representa una variable de animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationVariable;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Construye un objeto de variable de animación.|  
|[CAnimationVariable:: ~ CAnimationVariable](#canimationvariable__~canimationvariable)|Destructor. Se llama cuando se destruye un objeto CAnimationVariable.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
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
|[CAnimationVariable::GetValue](#getvalue)|Sobrecargado. Devuelve el valor actual de la variable de animación.|  
|[CAnimationVariable::GetVariable](#getvariable)|Devuelve un puntero al objeto COM de IUIAnimationVariable.|  
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado y libera el objeto COM de IUIAnimationVariable.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Establece la relación entre una variable de animación y un objeto de animación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Especifica si se deben eliminar los objetos relacionados de transición.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.|  
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Contiene una lista de transiciones que animar esta variable de animación.|  
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Un puntero a un objeto de animación que encapsula esta variable de animación.|  
|[CAnimationVariable::m_variable](#m_variable)|Almacena un puntero al objeto COM de IUIAnimationVariable. NULL si aún no ha creado el objeto COM, o si no se pudo crear.|  
  
## <a name="remarks"></a>Comentarios  
 La clase CAnimationVariable encapsula el objeto COM de IUIAnimationVariable. También contiene una lista de las transiciones que se aplicará a la variable de animación en un guión gráfico. Objetos de CAnimationVariable se incrustan a objetos de animación, que pueden representar en una aplicación de un valor animado, punto, tamaño, color y rectángulo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CAnimationVariable`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationvariable"></a>  CAnimationVariable:: ~ CAnimationVariable  
 Destructor. Se llama cuando se destruye un objeto CAnimationVariable.  
  
```  
virtual ~CAnimationVariable();
```  
  
##  <a name="addtransition"></a>  CAnimationVariable::AddTransition  
 Agrega una transición.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Parámetros  
 *pTransition*  
 Un puntero a una transición a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método para agregar una transición a la lista interna de transiciones que se aplicará a la variable de animación. Esta lista se debe eliminar cuando se ha programado una animación.  
  
##  <a name="applytransitions"></a>  CAnimationVariable::ApplyTransitions  
 Agrega las transiciones de la lista interna en guiones gráficos.  
  
```  
void ApplyTransitions(
    CAnimationController* pController,  
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parámetros  
 *pController*  
 Un puntero al controlador de animación del elemento primario.  
  
 *pStoryboard*  
 Un puntero al guión gráfico.  
  
 *bDependOnKeyframes*  
 Es TRUE si este método debería agregar transiciones que dependen de los fotogramas clave.  
  
### <a name="remarks"></a>Comentarios  
 Este método agrega las transiciones de la lista interna en guiones gráficos. Se llama desde el código de nivel superior varias veces para agregar transiciones que no dependen de los fotogramas clave y agregar transiciones que dependen de los fotogramas clave. Si la variable de animación objeto COM subyacente no se ha creado, este método crea en esta fase.  
  
##  <a name="canimationvariable"></a>  CAnimationVariable::CAnimationVariable  
 Construye un objeto de variable de animación.  
  
```  
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```  
  
### <a name="parameters"></a>Parámetros  
 *dblDefaultValue*  
 Especifica el valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Construye un objeto de variable de animación y establece su valor predeterminado. Un valor predeterminado se utiliza cuando una variable no se anima o no se pueden animar.  
  
##  <a name="cleartransitions"></a>  CAnimationVariable::ClearTransitions  
 Borra las transiciones.  
  
```  
void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parámetros  
 *bAutodestroy*  
 Especifica si este método debe eliminar objetos de transición.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita todas las transiciones de la lista interna de transiciones. Si bAutodestroy es TRUE, o m_bAutodestroyTransitions es TRUE, se eliminan las transiciones. En caso contrario, el llamador debe cancelar la asignación de los objetos de transición.  
  
##  <a name="create"></a>  CAnimationVariable::Create  
 Crea el objeto subyacente de COM de variable de animación.  
  
```  
virtual BOOL Create(IUIAnimationManager* pManager);
```  
  
### <a name="parameters"></a>Parámetros  
 *pManager*  
 Un puntero al administrador de animación.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la variable de animación se creó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea la variable de animación objeto COM subyacente y establece su valor predeterminado.  
  
##  <a name="createtransitions"></a>  CAnimationVariable::CreateTransitions  
 Crea todas las transiciones que se aplicará a esta variable de animación.  
  
```  
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parámetros  
*pLibrary*  
 Un puntero a un [IUIAnimationTransitionLibrary interfaz](https://msdn.microsoft.com/library/windows/desktop/dd371897), que define una biblioteca de transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si las transiciones se crean correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando es necesario crear transiciones que se han agregado a la lista interna de la variable de transiciones.  
  
##  <a name="enableintegervaluechangedevent"></a>  CAnimationVariable::EnableIntegerValueChangedEvent  
 Habilita o deshabilita el evento IntegerValueChanged.  
  
```  
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 *pController*  
 Un puntero al controlador principal.  
  
 *bHabilitar el*  
 TRUE: Habilitar eventos, FALSE - deshabilitar eventos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita el evento ValueChanged, el marco de trabajo llama a método virtual CAnimationController::OnAnimationIntegerValueChanged. Debe invalidarlo en una clase derivada de CAnimationController para procesar este evento. Este método se llama cada vez que se cambia el valor del entero de variable de animación.  
  
##  <a name="enablevaluechangedevent"></a>  CAnimationVariable::EnableValueChangedEvent  
 Habilita o deshabilita el evento ValueChanged.  
  
```  
void EnableValueChangedEvent (
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 *pController*  
 Un puntero al controlador principal.  
  
 *bHabilitar el*  
 TRUE: Habilitar eventos, FALSE - deshabilitar eventos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita el evento ValueChanged, el marco de trabajo llama a método virtual CAnimationController::OnAnimationValueChanged. Debe invalidarlo en una clase derivada de CAnimationController para procesar este evento. Este método se llama cada vez que se cambia el valor de variable de animación.  
  
##  <a name="getdefaultvalue"></a>  CAnimationVariable::GetDefaultValue  
 Devuelve el valor predeterminado.  
  
```  
DOUBLE GetDefaultValue() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para obtener el valor predeterminado de la variable de animación. El valor predeterminado se puede establecer en el constructor o método SetDefaultValue.  
  
##  <a name="getparentanimationobject"></a>  CAnimationVariable::GetParentAnimationObject  
 Devuelve el principal objeto de animación.  
  
```  
CAnimationBaseObject* GetParentAnimationObject();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de animación primario, si se ha establecido la relación, en caso contrario, es NULL.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede llamarse para recuperar un puntero a un objeto de animación primario (contenedor).  
  
##  <a name="getvalue"></a>  CAnimationVariable::GetValue  
 Devuelve el valor actual de la variable de animación.  
  
```  
HRESULT GetValue(DOUBLE& dblValue);  
HRESULT GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *dblValue*  
 El valor actual de la variable de animación.  
  
 *nvalor*  
 El valor actual de la variable de animación.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el valor se obtuvo correctamente o no se ha creado la variable de animación subyacente. Código de error HRESULT en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede llamarse para recuperar el valor actual de la variable de animación. Si no se ha creado el objeto COM subyacente, dblValue contendrá un valor predeterminado, cuando la función devuelve.  
  
##  <a name="getvariable"></a>  CAnimationVariable::GetVariable  
 Devuelve un puntero al objeto COM de IUIAnimationVariable.  
  
```  
IUIAnimationVariable* GetVariable();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido al objeto COM IUIAnimationVariable, o NULL si no se creó la variable de animación, o no se puede crear.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función para obtener acceso al objeto IUIAnimationVariable COM subyacente y llamar a sus métodos directamente si es necesario.  
  
##  <a name="m_bautodestroytransitions"></a>  CAnimationVariable::m_bAutodestroyTransitions  
 Especifica si se deben eliminar los objetos relacionados de transición.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer este valor como True para forzar la eliminación de objetos de transición cuando se eliminan de la lista de transiciones interna. Si este valor es FALSE, las transiciones deben eliminarse mediante una llamada a la aplicación. La lista de transiciones siempre se borra después de que se ha programado una animación. El valor predeterminado es FALSE.  
  
##  <a name="m_dbldefaultvalue"></a>  CAnimationVariable::m_dblDefaultValue  
 Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.  
  
```  
DOUBLE m_dblDefaultValue;  
```  
  
##  <a name="m_lsttransitions"></a>  CAnimationVariable::m_lstTransitions  
 Contiene una lista de transiciones que animar esta variable de animación.  
  
```  
CObList m_lstTransitions;  
```  
  
##  <a name="m_pparentobject"></a>  CAnimationVariable::m_pParentObject  
 Un puntero a un objeto de animación que encapsula esta variable de animación.  
  
```  
CAnimationBaseObject* m_pParentObject;  
```  
  
##  <a name="m_variable"></a>  CAnimationVariable::m_variable  
 Almacena un puntero al objeto COM de IUIAnimationVariable. NULL si aún no ha creado el objeto COM, o si no se pudo crear.  
  
```  
ATL::CComPtr<IUIAnimationVariable> m_variable;  
```  
  
##  <a name="setdefaultvalue"></a>  CAnimationVariable::SetDefaultValue  
 Establece el valor predeterminado y libera el objeto COM de IUIAnimationVariable.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *dblDefaultValue*  
 Especifica el nuevo valor predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para restablecer el valor predeterminado. Este método libera el objeto COM IUIAnimationVariable interno, por lo tanto, cuando se vuelve a crear la variable de animación, el objeto COM subyacente obtiene el nuevo valor predeterminado. El valor predeterminado es devuelto por GetValue si no se crea el objeto COM que representa la variable de animación, o si no se ha animado la variable.  
  
##  <a name="setparentanimationobject"></a>  CAnimationVariable::SetParentAnimationObject  
 Establece la relación entre una variable de animación y un objeto de animación.  
  
```  
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```  
  
### <a name="parameters"></a>Parámetros  
 *pParentObject*  
 Un puntero a un objeto de animación que contiene esta variable.  
  
### <a name="remarks"></a>Comentarios  
 Se llama internamente a este método para establecer una relación uno a uno entre una variable de animación y un objeto de animación que encapsula.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
