---
title: Clase CCustomInterpolator | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
dev_langs:
- C++
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b093ff87d7f2c8c52b6745be4e2a31580fce0fce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ccustominterpolator-class"></a>Clase CCustomInterpolator
Implementa un interpolador básico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Sobrecargado. Construye un objeto personalizado interpolador e inicializa la duración y el progreso en los valores especificados.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador.|  
|[CCustomInterpolator::GetDuration](#getduration)|Obtiene la duración del interpolador.|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Obtiene el valor final que conduce el interpolador.|  
|[CCustomInterpolator::Init](#init)|Inicializa el valor final y la duración.|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento dado.|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpola el progreso en un desplazamiento dado|  
|[CCustomInterpolator::SetDuration](#setduration)|Establece la duración del interpolador.|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y el progreso de la interpolador.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|El valor de interpolación.|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|El progreso de la interpolación.|  
|[CCustomInterpolator::m_duration](#m_duration)|La duración de la transición.|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|El valor final de una variable al final de la transición.|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|El valor de la variable al principio de la transición.|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|El progreso de la variable al principio de la transición.|  
  
## <a name="remarks"></a>Comentarios  
 Derivar una clase de CCustomInterpolator y reemplazar todos los métodos necesarios para implementar un algoritmo de interpolación personalizado. Un puntero a esta clase se debe pasar como parámetro a CCustomTransition.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>  CCustomInterpolator::CCustomInterpolator  
 Construye un objeto personalizado interpolador y establece todos los valores para el valor predeterminado es 0.  
  
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
  
##  <a name="getdependencies"></a>  CCustomInterpolator::GetDependencies  
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
 Salida. Aspectos del interpolador que dependen de la velocidad inicial pasan a SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Salida. Aspectos del interpolador que dependen de la duración se pasan a SetDuration.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
##  <a name="getduration"></a>  CCustomInterpolator::GetDuration  
 Obtiene la duración del interpolador.  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 Salida. La duración de la transición, en segundos.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
##  <a name="getfinalvalue"></a>  CCustomInterpolator::GetFinalValue  
 Obtiene el valor final que conduce el interpolador.  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>Parámetros  
 `value`  
 Salida. El valor final de una variable al final de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
##  <a name="init"></a>  CCustomInterpolator::Init  
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
  
##  <a name="interpolatevalue"></a>  CCustomInterpolator::InterpolateValue  
 Interpola el valor en un desplazamiento dado.  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>Parámetros  
 `value`  
 Salida. El valor de interpolación.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
##  <a name="interpolatevelocity"></a>  CCustomInterpolator::InterpolateVelocity  
 Interpola el progreso en un desplazamiento dado  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `velocity`  
 Salida. El progreso de la variable en el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
##  <a name="m_currentvalue"></a>  CCustomInterpolator::m_currentValue  
 El valor de interpolación.  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="m_currentvelocity"></a>  CCustomInterpolator::m_currentVelocity  
 El progreso de la interpolación.  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="m_duration"></a>  CCustomInterpolator::m_duration  
 La duración de la transición.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>  CCustomInterpolator::m_finalValue  
 El valor final de una variable al final de la transición.  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="m_initialvalue"></a>  CCustomInterpolator::m_initialValue  
 El valor de la variable al principio de la transición.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>  CCustomInterpolator::m_initialVelocity  
 El progreso de la variable al principio de la transición.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>  CCustomInterpolator::SetDuration  
 Establece la duración del interpolador.  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
##  <a name="setinitialvalueandvelocity"></a>  CCustomInterpolator::SetInitialValueAndVelocity  
 Establece el valor inicial y el progreso de la interpolador.  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialValue`  
 El valor de la variable al principio de la transición.  
  
 `initialVelocity`  
 El progreso de la variable al principio de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación básica siempre devuelve TRUE. Devolver FALSE de implementación invalidada si desea producirá un error en el evento.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
