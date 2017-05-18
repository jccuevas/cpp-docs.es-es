---
title: Clase CInterpolatorBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
dev_langs:
- C++
helpviewer_keywords:
- CInterpolatorBase class
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
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
ms.openlocfilehash: 44c67eef38b34a2a3cf677b42a40304c01668b42
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cinterpolatorbase-class"></a>Clase CInterpolatorBase
Implementa una devolución de llamada, a la que llama la API de animación cuando tiene que calcular un nuevo valor de una variable de animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Construye el `CInterpolatorBase` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CInterpolatorBase::CreateInstance](#createinstance)|Crea una instancia de `CInterpolatorBase` y almacena un puntero a interpolador personalizado, que se pueden controlar los eventos.|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDependencies`).|  
|[CInterpolatorBase::GetDuration](#getduration)|Obtiene la duración del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDuration`).|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Obtiene el valor final a la que lleva el interpolador. (Invalida `CUIAnimationInterpolatorBase::GetFinalValue`).|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento dado (reemplaza `CUIAnimationInterpolatorBase::InterpolateValue`.)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpola la velocidad en un desplazamiento dado (reemplaza `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Almacena un puntero a interpolador personalizado, que se pueden controlar los eventos.|  
|[CInterpolatorBase::SetDuration](#setduration)|Establece la duración del interpolador (reemplaza `CUIAnimationInterpolatorBase::SetDuration`.)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y el progreso de la interpolador. (Invalida `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|  
  
## <a name="remarks"></a>Comentarios  
 Este controlador se crea y se pasa a `IUIAnimationTransitionFactory::CreateTransition` cuando un `CCustomTransition` se crea el objeto como parte del proceso de inicialización de animación (iniciado por `CAnimationController::AnimateGroup`). Normalmente no es necesario usar esta clase directamente, simplemente lo enruta todos los eventos en un `CCustomInterpolator`-cuyo puntero se pasa al constructor de clase derivada `CCustomTransition`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase  
 Construye el objeto CInterpolatorBase.  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>CInterpolatorBase::CreateInstance  
 Crea una instancia de CInterpolatorBase y almacena un puntero a interpolador personalizado, que se pueden controlar los eventos.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>Parámetros  
 `pInterpolator`  
 Puntero a un interpolador personalizado.  
  
 `ppHandler`  
 Salida. Cuando la función devuelve, contiene un puntero a la instancia de CInterpolatorBase.  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 Obtiene las dependencias del interpolador.  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialValueDependencies`  
 Salida. Aspectos del interpolador que dependen del valor inicial que se pasan a SetInitialValueAndVelocity.  
  
 `initialVelocityDependencies`  
 Salida. Aspectos del interpolador que dependen de la velocidad inicial que se pasan a SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Salida. Aspectos del interpolador que dependen de la duración se pasan a SetDuration.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método GetDependencies devuelve E_FAIL.  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 Obtiene la duración del interpolador.  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 Salida. La duración de la transición en segundos.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método GetDuration devuelve E_FAIL.  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 Obtiene el valor final a la que lleva el interpolador.  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parámetros  
 `value`  
 Salida. El valor final de una variable al final de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método GetFinalValue devuelve E_FAIL.  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 Interpola el valor en un desplazamiento dado  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parámetros  
 `offset`  
 Desplazamiento desde el inicio de la transición. El desplazamiento es siempre mayor o igual que cero y menor que la duración de la transición. No se llama a este método si la duración de la transición es cero.  
  
 `value`  
 Salida. El valor interpolado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método InterpolateValue devuelve E_FAIL.  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 Interpola la velocidad en un desplazamiento dado  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `offset`  
 Desplazamiento desde el inicio de la transición. El desplazamiento es siempre mayor o igual que cero y menor o igual a la duración de la transición. No se llama a este método si la duración de la transición es cero.  
  
 `velocity`  
 Salida. La velocidad de la variable en el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método InterpolateVelocity devuelve E_FAIL.  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 Almacena un puntero a interpolador personalizado, que se pueden controlar los eventos.  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parámetros  
 `pInterpolator`  
 Puntero a un interpolador personalizado.  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 Establece la duración del interpolador  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parámetros  
 `duration`  
 La duración de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método SetDuration devuelve E_FAIL.  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 Establece el valor inicial y el progreso de la interpolador.  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parámetros  
 `initialValue`  
 El valor de la variable en el inicio de la transición.  
  
 `initialVelocity`  
 La velocidad de la variable en el inicio de la transición.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada devuelve FALSE desde el método SetInitialValueAndVelocity devuelve E_FAIL.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

