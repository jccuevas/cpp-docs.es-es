---
title: Clase CAnimationStoryboardEventHandler | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb7c89e6441379949386baecbddbb30f7c01ebff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352228"
---
# <a name="canimationstoryboardeventhandler-class"></a>Clase CAnimationStoryboardEventHandler
Implementa una devolución de llamada, a la que llama la API de animación cuando se cambia el estado de un guión gráfico o se actualiza.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Construye un objeto `CAnimationStoryboardEventHandler`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Crea una instancia de `CAnimationStoryboardEventHandler` devolución de llamada.|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Controla `OnStoryboardStatusChanged` eventos, que se producen cuando cambia el estado de un guión gráfico (invalidaciones `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`.)|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|Controla `OnStoryboardUpdated` eventos, que se producen cuando se actualiza (invalidaciones `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.)|  
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para eventos de ruta.|  
  
## <a name="remarks"></a>Comentarios  
 Este controlador de eventos se crea y se pasa a `IUIAnimationStoryboard::SetStoryboardEventHandler` método, cuando se llama a `CAnimationController::EnableStoryboardEventHandler`.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="canimationstoryboardeventhandler"></a>  CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler  
 Construye un objeto CAnimationStoryboardEventHandler.  
  
```  
CAnimationStoryboardEventHandler();
```  
  
##  <a name="createinstance"></a>  CAnimationStoryboardEventHandler::CreateInstance  
 Crea una instancia de devolución de llamada de CAnimationStoryboardEventHandler.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationStoryboardEventHandler** ppHandler);
```  
  
### <a name="parameters"></a>Parámetros  
 `pAnimationController`  
 Un puntero al controlador de animación, que recibe eventos.  
  
 `ppHandler`  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.  
  
##  <a name="onstoryboardstatuschanged"></a>  CAnimationStoryboardEventHandler::OnStoryboardStatusChanged  
 Controla los eventos OnStoryboardStatusChanged, que se producen cuando cambia el estado de un guión gráfico  
  
```  
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parámetros  
 `storyboard`  
 Un puntero al guión gráfico cuyo estado ha cambiado.  
  
 `newStatus`  
 Especifica el nuevo estado de guión gráfico.  
  
 `previousStatus`  
 Especifica el estado de guión gráfico anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito; en caso contrario E_FAIL.  
  
##  <a name="onstoryboardupdated"></a>  CAnimationStoryboardEventHandler::OnStoryboardUpdated  
 Controla los eventos OnStoryboardUpdated, que se producen cuando se actualiza un guión gráfico  
  
```  
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```  
  
### <a name="parameters"></a>Parámetros  
 `storyboard`  
 Un puntero al guión gráfico, que se ha actualizado.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito; en caso contrario E_FAIL.  
  
##  <a name="setanimationcontroller"></a>  CAnimationStoryboardEventHandler::SetAnimationController  
 Almacena un puntero al controlador de animación para eventos de ruta.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parámetros  
 `pAnimationController`  
 Un puntero al controlador de animación, que recibe eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
