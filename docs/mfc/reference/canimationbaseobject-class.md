---
title: Clase CAnimationBaseObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationBaseObject class
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
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
ms.openlocfilehash: c714c78b7017ed314b30f64df4bfceb587226c15
ms.lasthandoff: 02/24/2017

---
# <a name="canimationbaseobject-class"></a>Clase CAnimationBaseObject
La clase base para todos los objetos de animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Sobrecargado. Construye un objeto de animación.|  
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|Destructor. Se llama cuando se destruye un objeto de animación.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Agrega transiciones con encapsulado animación de guión gráfico.|  
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Quita todas las transiciones relacionadas.|  
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Determina si un objeto de animación contiene una variable de animación determinado.|  
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Crea las transiciones asociados con un objeto de animación.|  
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Desasocia un objeto de animación de controlador de animación principal.|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Configura el controlador de eventos cambia de valor entero.|  
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Establece el valor cambiado el controlador de eventos.|  
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Indica si la transición relacionada se destruyen automáticamente.|  
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Devuelve el identificador del grupo.|  
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Devuelve el identificador del objeto actual.|  
|[CAnimationBaseObject::GetUserData](#getuserdata)|Devuelve los datos definidos por el usuario.|  
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Establece una marca que ordena a destruir automáticamente las transiciones.|  
|[CAnimationBaseObject::SetID](#setid)|Establece nuevos identificadores.|  
|[CAnimationBaseObject::SetUserData](#setuserdata)|Conjuntos de datos.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Recopila los punteros a variables de animación independiente.|  
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Establece la relación entre las variables de animación, contenidas en un objeto de animación y su contenedor.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Especifica si se deben destruir automáticamente transiciones relacionadas.|  
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Almacena los datos definidos por el usuario.|  
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Especifica el identificador de grupo del objeto de animación.|  
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Especifica el identificador de objeto del objeto de animación.|  
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Un puntero en el controlador de animación principal.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase implementa los métodos básicos para todos los objetos de animación. Un objeto de animación puede representar un valor, el punto, el tamaño, el rectángulo o el color en una aplicación, así como cualquier entidad personalizada. Objetos de animación se almacenan en grupos de animación (consulte CAnimationGroup). Cada grupo se puede animar por separado y se puede tratar como un análogo del guión gráfico. Un objeto de animación encapsula una o más animación variables (consulte CAnimationVariable), dependiendo de su representación lógica. Por ejemplo, CAnimationRect contiene cuatro variables de animación: una variable para cada lado del rectángulo. Cada clase de objeto de animación expone el método AddTransition sobrecargado, que debe usarse para aplicar transiciones a variables de animación encapsulado. Un objeto de animación se puede identificar por Id. de objeto (opcionalmente) y por el identificador de grupo. Un identificador de grupo es necesario para colocar un objeto de animación para el grupo correcto, pero si no se especifica un identificador de grupo, un objeto se coloca en el grupo predeterminado con el Id. 0. Si se llama a SetID con GroupID diferente, un objeto de animación se moverá a otro grupo (se crea un nuevo grupo si es necesario).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationBaseObject`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject:: ~ CAnimationBaseObject  
 Destructor. Se llama cuando se destruye un objeto de animación.  
  
```  
virtual ~CAnimationBaseObject();
```  
  
##  <a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions  
 Agrega transiciones con encapsulado animación de guión gráfico.  
  
```  
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStoryboard`  
 Un puntero a un guión gráfico.  
  
 `bDependOnKeyframes`  
 Con FALSE, este método agrega sólo las transiciones que no dependen de los fotogramas clave.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si las transiciones se agregaron correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Agrega transiciones relacionadas, que se han agregado con AddTransition (métodos sobrecargados en clases derivadas) en guiones gráficos.  
  
##  <a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject  
 Construye un objeto de animación.  
  
```  
CAnimationBaseObject();

 
CAnimationBaseObject(
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nGroupID`  
 Especifica el identificador de grupo.  
  
 `nObjectID`  
 Especifica el identificador de objeto.  
  
 `dwUserData`  
 Datos definidos por el usuario, que pueden asociados con el objeto de animación y recuperarse más adelante en tiempo de ejecución.  
  
### <a name="remarks"></a>Comentarios  
 Construye un objeto de animación y asigna el identificador de objeto predeterminado (0) y el identificador de grupo (0).  
  
##  <a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions  
 Quita todas las transiciones relacionadas.  
  
```  
virtual void ClearTransitions(BOOL bAutodestroy);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAutodestroy`  
 Especifica si se debe destruir objetos de transición automáticamente, o simplemente quitarlos de la lista relacionada.  
  
### <a name="remarks"></a>Comentarios  
 Quita todos ellos relacionados con transiciones y destruyendo si marca bAutodestroy o m_bAutodestroyTransitions es TRUE. Las transiciones se deben destruir automáticamente sólo si no se asignan en la pila. Si las marcas anteriores son FALSE, las transiciones sólo se quitan de la lista interna de transiciones relacionadas.  
  
##  <a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable  
 Determina si un objeto de animación contiene una variable de animación determinado.  
  
```  
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parámetros  
 `pVariable`  
 Puntero a la variable de animación.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la variable de animación se encuentra en el objeto de animación; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para determinar si una variable de animación especificada por pVariable está dentro de un objeto de animación. Un objeto de animación, dependiendo de su tipo, puede contener varias variables de animación. Por ejemplo, CAnimationColor contiene tres variables, uno para cada componente de color (rojo, verde y azul). Cuando ha cambiado un valor de animación, API de animación de Windows envía eventos ValueChanged o IntegerValueChanged (si está habilitado) y el parámetro de este evento es un puntero a interfaz IUIAnimationVariable de animación. Este método ayuda a obtener un puntero a la animación de un puntero al objeto COM de contenido.  
  
##  <a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions  
 Crea las transiciones asociados con un objeto de animación.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si las transiciones se crearon correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Recorre la lista de variables de animación encapsulado en un objeto derivado de animación y crea las transiciones asociados con cada variable de animación.  
  
##  <a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController  
 Desasocia un objeto de animación de controlador de animación principal.  
  
```  
void DetachFromController();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa internamente.  
  
##  <a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent  
 Configura el controlador de eventos cambia de valor entero.  
  
```  
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 `pController`  
 Puntero a un controlador principal.  
  
 `bEnable`  
 Especifica si desea habilitar o deshabilitar eventos de cambio de valor de entero.  
  
### <a name="remarks"></a>Comentarios  
 Si está habilitado el controlador de eventos cambia de valor entero, puede controlar este evento en el método CAnimationController::OnAnimationIntegerValueChanged, que se debe invalidar en una clase derivada de CAnimationController. Este método se llama cada vez que cambia el valor del entero de animación.  
  
##  <a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent  
 Establece el valor cambiado el controlador de eventos.  
  
```  
virtual void EnableValueChangedEvent(
    CAnimationController* pController,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 `pController`  
 Puntero a un controlador principal.  
  
 `bEnable`  
 Especifica si desea habilitar o deshabilitar eventos de cambio de valor.  
  
### <a name="remarks"></a>Comentarios  
 Si está habilitado el controlador de eventos cambia de valor, puede controlar este evento en el método CAnimationController::OnAnimationValueChanged, que se debe invalidar en una clase derivada de CAnimationController. Este método se llama cada vez que cambia el valor de la animación.  
  
##  <a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList  
 Recopila los punteros a variables de animación independiente.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lst`  
 Una lista que se debe rellenar con variables de animación incluidas en un objeto de animación.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un método virtual puro que se debe invalidar en una clase derivada. Un objeto de animación, dependiendo de su tipo, contiene una o más variables de animación. Por ejemplo, CAnimationPoint contiene dos variables de coordenadas X e Y respectivamente. La clase base CAnimationBaseObject implementa algunos métodos genéricos que actúan en una lista de variables de animación: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Estos métodos llamada GetAnimationVariableList, que se rellena en una clase derivada con variables de animación real contenidas en un objeto de animación determinado, a continuación, recorrer la lista y realizan las acciones necesarias. Si crea un objeto de animación personalizada, debe agregar a lst todas las variables de animación contenidas en el objeto.  
  
##  <a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions  
 Indica si la transición relacionada se destruyen automáticamente.  
  
```  
BOOL GetAutodestroyTransitions() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es TRUE, las transiciones relacionadas se destruyen automáticamente; Si es FALSE, los objetos de transición deben desasignarse mediante una llamada a la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta marca es TRUE. Establezca esta marca únicamente si ha asignado la transición en la pila o transiciones deben desasignarse por la aplicación que realiza la llamada.  
  
##  <a name="getgroupid"></a>CAnimationBaseObject::GetGroupID  
 Devuelve el identificador del grupo.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de grupo actual.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para recuperar el identificador de grupo. 'S 0 si el Id. de grupo no se estableció explícitamente en el constructor o con SetID.  
  
##  <a name="getobjectid"></a>CAnimationBaseObject::GetObjectID  
 Devuelve el identificador del objeto actual.  
  
```  
UINT32 GetObjectID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Id. de objeto actual.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para recuperar el identificador de objeto. 'S 0 si el Id. de objeto no se estableció explícitamente en el constructor o con SetID.  
  
##  <a name="getuserdata"></a>CAnimationBaseObject::GetUserData  
 Devuelve los datos definidos por el usuario.  
  
```  
DWORD GetUserData() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de datos personalizados.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para recuperar los datos personalizados en tiempo de ejecución. El valor devuelto será 0 si no se inicializó explícitamente en el constructor o con SetUserData.  
  
##  <a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions  
 Especifica si se deben destruir automáticamente transiciones relacionadas.  
  
```  
BOOL m_bAutodestroyTransitions;  
```  
  
##  <a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData  
 Almacena los datos definidos por el usuario.  
  
```  
DWORD m_dwUserData;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID  
 Especifica el identificador de grupo del objeto de animación.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID  
 Especifica el identificador de objeto del objeto de animación.  
  
```  
UINT32 m_nObjectID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController  
 Un puntero en el controlador de animación principal.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions  
 Establece una marca que ordena a destruir automáticamente las transiciones.  
  
```  
void SetAutodestroyTransitions(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `bValue`  
 Especifica el auto destruir marca.  
  
### <a name="remarks"></a>Comentarios  
 Establezca esta marca únicamente si asigna objetos mediante el operador nuevo. Si por algún motivo se asignan objetos de transición en la pila, se destruye automáticamente marca debe ser FALSE. De forma predeterminada, esta marca es TRUE.  
  
##  <a name="setid"></a>CAnimationBaseObject::SetID  
 Establece nuevos identificadores.  
  
```  
void SetID(
    UINT32 nObjectID,  
    UINT32 nGroupID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nObjectID`  
 Especifica el identificador de objeto nuevo.  
  
 `nGroupID`  
 Especifica el nuevo identificador de grupo.  
  
### <a name="remarks"></a>Comentarios  
 Permite cambiar el identificador de objeto y el identificador de grupo. Si el nuevo identificador de grupo difiere el identificador actual, un objeto de animación se mueve a otro grupo (un nuevo grupo se creará, si es necesario).  
  
##  <a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects  
 Establece la relación entre las variables de animación, contenidas en un objeto de animación y su contenedor.  
  
```  
virtual void SetParentAnimationObjects();
```  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una aplicación auxiliar que puede utilizarse para establecer una relación entre las variables de animación, incluidos en un objeto de animación y su contenedor. Ejecuta un bucle sobre las variables de animación y establece un puntero a un objeto de animación principal a cada variable de animación. En la implementación actual de que la relación real se establece en CAnimationBaseObject::ApplyTransitions, por lo tanto, los punteros alternativos no se establecen hasta que se llama CAnimationGroup::Animate. Conocer la relación puede ser útil cuando se usa procesamiento de eventos y la necesidad de obtener una animación principal objeto de CAnimationVariable (use CAnimationVariable::GetParentAnimationObject).  
  
##  <a name="setuserdata"></a>CAnimationBaseObject::SetUserData  
 Conjuntos de datos.  
  
```  
void SetUserData (DWORD dwUserData);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwUserData`  
 Especifica los datos personalizados.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para asociar un datos personalizados a un objeto de animación. Estos datos se pueden recuperar más tarde en tiempo de ejecución mediante GetUserData.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

