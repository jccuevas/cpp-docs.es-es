---
title: Clase CAnimationVariableChangeHandler | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58646efaaa0087be2bd73e45acd8ade4a16e9767
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957096"
---
# <a name="canimationvariablechangehandler-class"></a>Clase CAnimationVariableChangeHandler
Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Construye un objeto `CAnimationVariableChangeHandler`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|Crea una instancia de `CAnimationVariableChangeHandler` objeto.|  
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Se llama cuando cambia un valor de una variable de animación. (Invalida `CUIAnimationVariableChangeHandlerBase::OnValueChanged`).|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para eventos de ruta.|  
  
## <a name="remarks"></a>Comentarios  
 Este controlador de eventos se crea y se pasa a `IUIAnimationVariable::SetVariableChangeHandler` método, cuando se llama a `CAnimationVariable::EnableValueChangedEvent` o `CAnimationBaseObject::EnableValueChangedEvent` (lo que permite este evento para todas las variables de animación que se encapsula en un objeto de animación).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged  
 Se llama cuando cambia un valor de una variable de animación.  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>Parámetros  
 *guión gráfico*  
 El guión gráfico que anima la variable.  
  
 *Variable*  
 La variable de animación que se ha actualizado.  
  
 *newValue*  
 Nuevo valor.  
  
 *previousValue*  
 El valor anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController  
 Almacena un puntero al controlador de animación para eventos de ruta.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parámetros  
 *pAnimationController*  
 Un puntero al controlador de animación, que recibe eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
