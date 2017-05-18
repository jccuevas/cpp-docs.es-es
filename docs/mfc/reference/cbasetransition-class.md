---
title: Clase CBaseTransition | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
dev_langs:
- C++
helpviewer_keywords:
- CBaseTransition class
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b979d03587ada42486d0462733dfe6fd22f9f7cc
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cbasetransition-class"></a>Clase CBaseTransition
Representa una transición básica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBaseTransition : public CObject;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-enumerations"></a>Enumeraciones públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseTransition::TRANSITION_TYPE (enumeración)](#transition_type_enumeration)|Define los tipos de transición compatibles actualmente con la implementación de MFC de la API de animación de Windows.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](#cbasetransition)|Construye un objeto de base de transición.|  
|[CBaseTransition:: ~ CBaseTransition](#cbasetransition__~cbasetransition)|Destructor. Se llama cuando se destruye un objeto de la transición.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Agrega una transición a un guión gráfico.|  
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Agrega una transición a un guión gráfico.|  
|[CBaseTransition::Clear](#clear)|Versiones encapsulan el objeto COM IUIAnimationTransition.|  
|[CBaseTransition::Create](#create)|Crea una transición de COM.|  
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Devuelve el fotograma clave de inicio.|  
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Devuelve un puntero a una variable relacionada.|  
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Devuelve el fotograma clave de inicio.|  
|[CBaseTransition::GetTransition](#gettransition)|Sobrecargado. Devuelve un puntero al objeto de la transición de COM subyacente.|  
|[CBaseTransition::GetType](#gettype)|Devuelve el tipo de transición.|  
|[CBaseTransition::IsAdded](#isadded)|Indica si se ha agregado una transición a un guión gráfico.|  
|[CBaseTransition::SetKeyframes](#setkeyframes)|Establece los fotogramas clave para una transición.|  
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Establece una relación entre la variable de animación y transición.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBaseTransition::m_bAdded](#m_badded)|Especifica si se ha agregado una transición a un guión gráfico.|  
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Almacena un puntero al fotograma clave que especifica el final de la transición.|  
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Puntero a una variable de animación, se anima a la transición que se almacena en m_transition.|  
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Almacena un puntero al fotograma clave que especifica el comienzo de la transición.|  
|[CBaseTransition::m_transition](#m_transition)|Almacena un puntero a IUIAnimationTransition. Es NULL si no se ha creado un objeto de la transición de COM.|  
|[CBaseTransition::m_type](#m_type)|Almacena el tipo de transición.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase encapsula la interfaz IUIAnimationTransition y sirve como clase base para todas las transiciones.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseTransition`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="_dtorcbasetransition"></a>CBaseTransition:: ~ CBaseTransition  
 Destructor. Se llama cuando se destruye un objeto de la transición.  
  
```  
virtual ~CBaseTransition();
```  
  
##  <a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard  
 Agrega una transición a un guión gráfico.  
  
```  
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStoryboard`  
 Puntero al guión gráfico, que se animará la variable relacionada.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se agregó correctamente a un guión gráfico.  
  
### <a name="remarks"></a>Comentarios  
 Aplica la transición a la variable relacionada en el guión gráfico. Si esta es la primera transición que se aplica a esta variable en este guión gráfico, la transición empieza en el principio del guión gráfico. De lo contrario, la transición se anexa a la transición de agregado más recientemente a la variable.  
  
##  <a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes  
 Agrega una transición a un guión gráfico.  
  
```  
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStoryboard`  
 Puntero al guión gráfico, que se animará la variable relacionada.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la transición se agregó correctamente a un guión gráfico.  
  
### <a name="remarks"></a>Comentarios  
 Aplica la transición a la variable relacionada en el guión gráfico. Si se especificó el fotograma clave de inicio, la transición empieza en el fotograma clave. Si se especificó el fotograma clave final, la transición empieza en el fotograma clave de inicio y y se detiene en el fotograma clave final. Si la transición se creó con un parámetro de duración, esta duración se sobrescribe con la duración de tiempo entre los fotogramas clave de inicio y finalización. Si se ha especificado ningún fotograma clave, la transición se anexa a la transición de agregado más recientemente a la variable.  
  
##  <a name="cbasetransition"></a>CBaseTransition::CBaseTransition  
 Construye un objeto de base de transición.  
  
```  
CBaseTransition();
```  
  
##  <a name="clear"></a>CBaseTransition::Clear  
 Versiones encapsulan el objeto COM IUIAnimationTransition.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método debe llamarse desde el método de creación de una clase derivada para evitar la pérdida de la interfaz de IUITransition.  
  
##  <a name="create"></a>CBaseTransition::Create  
 Crea una transición de COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pLibrary`  
 Puntero a la biblioteca de transición, que crea transiciones estándares. Puede ser NULL para las transiciones personalizadas.  
  
 `pFactory`  
 Puntero al generador de transición, que crea transiciones personalizadas. Puede ser NULL para las transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si un objeto COM de transición se creó correctamente; de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una función virtual pura que se debe invalidar en una clase derivada. Lo llama el marco de una instancia del objeto de transición de COM subyacente.  
  
##  <a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe  
 Devuelve el fotograma clave de inicio.  
  
```  
CBaseKeyFrame* GetEndKeyframe();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a un fotograma clave, o NULL si no se debe insertar una transición entre fotogramas clave.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para tener acceso a un objeto de fotograma clave que estableció anteriormente SetKeyframes. Se llama al código de nivel superior cuando se agregan las transiciones al guión gráfico.  
  
##  <a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable  
 Devuelve un puntero a una variable relacionada.  
  
```  
CAnimationVariable* GetRelatedVariable();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a la variable de animación, o NULL si no ha establecido una variable de animación SetRelatedVariable.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un descriptor de acceso a la variable de animación relacionados.  
  
##  <a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe  
 Devuelve el fotograma clave de inicio.  
  
```  
CBaseKeyFrame* GetStartKeyframe();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a un fotograma clave, o NULL si no se debe iniciar una transición después de un fotograma clave.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para tener acceso a un objeto de fotograma clave que estableció anteriormente SetKeyframes. Se llama al código de nivel superior cuando se agregan las transiciones al guión gráfico.  
  
##  <a name="gettransition"></a>CBaseTransition::GetTransition  
 Devuelve un puntero al objeto de la transición de COM subyacente.  
  
```  
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* pFactory);  
  
IUIAnimationTransition* GetTransition();
```  
  
### <a name="parameters"></a>Parámetros  
 `pLibrary`  
 Puntero a la biblioteca de transición, que crea transiciones estándares. Puede ser NULL para las transiciones personalizadas.  
  
 `pFactory`  
 Puntero al generador de transición, que crea transiciones personalizadas. Puede ser NULL para las transiciones estándares.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a IUIAnimationTransition o NULL si no se puede crear la base de transición.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve un puntero al objeto de la transición de COM subyacente y lo crea si es necesario.  
  
##  <a name="gettype"></a>CBaseTransition::GetType  
 Devuelve el tipo de transición.  
  
```  
TRANSITION_TYPE GetType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de TRANSITION_TYPE valores enumerados.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para identificar un objeto de transición por su tipo. El tipo se establece en un constructor de una clase derivada.  
  
##  <a name="isadded"></a>CBaseTransition::IsAdded  
 Indica si se ha agregado una transición a un guión gráfico.  
  
```  
BOOL IsAdded();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ha agregado una transición a un guión gráfico, de lo contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este indicador se establece internamente cuando el código de nivel superior agrega las transiciones al guión gráfico.  
  
##  <a name="m_badded"></a>CBaseTransition::m_bAdded  
 Especifica si se ha agregado una transición a un guión gráfico.  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe  
 Almacena un puntero al fotograma clave que especifica el final de la transición.  
  
```  
CBaseKeyFrame* m_pEndKeyframe;  
```  
  
##  <a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable  
 Puntero a una variable de animación, se anima a la transición que se almacena en m_transition.  
  
```  
CAnimationVariable* m_pRelatedVariable;  
```  
  
##  <a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe  
 Almacena un puntero al fotograma clave que especifica el comienzo de la transición.  
  
```  
CBaseKeyFrame* m_pStartKeyframe;  
```  
  
##  <a name="m_transition"></a>CBaseTransition::m_transition  
 Almacena un puntero a IUIAnimationTransition. Es NULL si no se ha creado un objeto de la transición de COM.  
  
```  
ATL::CComPtr<IUIAnimationTransition> m_transition;  
```  
  
##  <a name="m_type"></a>CBaseTransition::m_type  
 Almacena el tipo de transición.  
  
```  
TRANSITION_TYPE m_type;  
```  
  
##  <a name="setkeyframes"></a>CBaseTransition::SetKeyframes  
 Establece los fotogramas clave para una transición.  
  
```  
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,  
    CBaseKeyFrame* pEnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStart`  
 Un fotograma clave que especifica el comienzo de la transición.  
  
 `pEnd`  
 Un fotograma clave que especifica el final de la transición.  
  
### <a name="remarks"></a>Comentarios  
 Este método indica la transición a iniciar después de fotograma clave especificado y, opcionalmente, si no es NULL, aplicará finalizar antes del fotograma clave especificado. Si la transición se creó con un parámetro de duración, esta duración se sobrescribe con la duración de tiempo entre los fotogramas clave de inicio y finalización.  
  
##  <a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable  
 Establece una relación entre la variable de animación y transición.  
  
```  
void SetRelatedVariable(CAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parámetros  
 `pVariable`  
 Puntero a la variable de animación relacionados.  
  
### <a name="remarks"></a>Comentarios  
 Establece una relación entre la variable de animación y transición. Una transición se puede aplicar sólo a una variable.  
  
##  <a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE (enumeración)  
 Define los tipos de transición compatibles actualmente con la implementación de MFC de la API de animación de Windows.  
  
```  
enum TRANSITION_TYPE;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo de transición se establece en el constructor de transición específica. Por ejemplo, CSinusoidalTransitionFromRange establece su tipo en SINUSOIDAL_FROM_RANGE.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

