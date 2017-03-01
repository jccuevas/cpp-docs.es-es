---
title: Clase CCustomInterpolator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CCustomInterpolator
- CCustomInterpolator
dev_langs:
- C++
helpviewer_keywords:
- CCustomInterpolator class
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 4d0b38543092dc68c2527f7e1385712164faf996
ms.lasthandoff: 02/24/2017

---
# <a name="ccustominterpolator-class"></a>Clase CCustomInterpolator
Implementa un interpolador básico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Sobrecargado. Construye un objeto personalizado interpolador e inicializa la duración y la velocidad en los valores especificados.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador.|  
|[CCustomInterpolator::GetDuration](#getduration)|Obtiene la duración del interpolador.|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Obtiene el valor final a la que lleva el interpolador.|  
|[CCustomInterpolator::Init](#init)|Inicializa el valor final y la duración.|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento dado.|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpola la velocidad en un desplazamiento dado|  
|[CCustomInterpolator::SetDuration](#setduration)|Establece la duración del interpolador.|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y el progreso de la interpolador.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|El valor interpolado.|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|La velocidad de la interpolación.|  
|[CCustomInterpolator::m_duration](#m_duration)|La duración de la transición.|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|El valor final de una variable al final de la transición.|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|El valor de la variable en el inicio de la transición.|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|La velocidad de la variable en el inicio de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Derivar una clase de CCustomInterpolator y reemplazar todos los métodos necesarios para implementar un algoritmo de interpolación personalizada. Un puntero a esta clase se debe pasar como parámetro al CCustomTransition.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-nameccustominterpolatora--ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator  
 Construye un objeto personalizado interpolador y establece todos los valores en el valor predeterminado 0.  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
 `finalValue`  
  
### <a name="remarks"></a>Comentarios  
 Utilice CCustomInterpolator::Init para inicializar la duración y el valor final más adelante en el código.  
  
##  <a name="a-namegetdependenciesa--ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator::GetDependencies  
 Obtiene las dependencias del interpolador.  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialValueDependencies`  
 Salida. Aspectos del interpolador que dependen del valor inicial que se pasan a SetInitialValueAndVelocity.  
  
 `initialVelocityDependencies`  
 Salida. Aspectos del interpolador que dependen de la velocidad inicial que se pasan a SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Salida. Aspectos del interpolador que dependen de la duración se pasan a SetDuration.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
##  <a name="a-namegetdurationa--ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration  
 Obtiene la duración del interpolador.  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 Salida. La duración de la transición en segundos.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
##  <a name="a-namegetfinalvaluea--ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue  
 Obtiene el valor final a la que lleva el interpolador.  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>Parámetros  
 `value`  
 Salida. El valor final de una variable al final de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
##  <a name="a-nameinita--ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init  
 Inicializa el valor final y la duración.  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
 `finalValue`  
 El valor final de una variable al final de la transición.  
  
##  <a name="a-nameinterpolatevaluea--ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue  
 Interpola el valor en un desplazamiento dado.  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>Parámetros  
 `value`  
 Salida. El valor interpolado.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
##  <a name="a-nameinterpolatevelocitya--ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity  
 Interpola la velocidad en un desplazamiento dado  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `velocity`  
 Salida. La velocidad de la variable en el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
##  <a name="a-namemcurrentvaluea--ccustominterpolatormcurrentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue  
 El valor interpolado.  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="a-namemcurrentvelocitya--ccustominterpolatormcurrentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity  
 La velocidad de la interpolación.  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="a-namemdurationa--ccustominterpolatormduration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="a-namemfinalvaluea--ccustominterpolatormfinalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue  
 El valor final de una variable al final de la transición.  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="a-nameminitialvaluea--ccustominterpolatorminitialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue  
 El valor de la variable en el inicio de la transición.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="a-nameminitialvelocitya--ccustominterpolatorminitialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity  
 La velocidad de la variable en el inicio de la transición.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="a-namesetdurationa--ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration  
 Establece la duración del interpolador.  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
##  <a name="a-namesetinitialvalueandvelocitya--ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity  
 Establece el valor inicial y el progreso de la interpolador.  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialValue`  
 El valor de la variable en el inicio de la transición.  
  
 `initialVelocity`  
 La velocidad de la variable en el inicio de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación básica siempre devuelve TRUE. Devolver FALSE desde la implementación invalidada si desea que se producirá un error en el evento.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

