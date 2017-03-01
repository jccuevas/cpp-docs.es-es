---
title: Clase CAnimationTimerEventHandler | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CAnimationTimerEventHandler
- CAnimationTimerEventHandler
dev_langs:
- C++
helpviewer_keywords:
- CAnimationTimerEventHandler class
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
caps.latest.revision: 18
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 5412c215caf85440e923e8a083ed310f8960849a
ms.lasthandoff: 02/24/2017

---
# <a name="canimationtimereventhandler-class"></a>Clase CAnimationTimerEventHandler
Implementa una devolución de llamada, a la que llama la API de animación cuando se producen eventos de control de tiempo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Crea una instancia de `CAnimationTimerEventHandler` devolución de llamada.|  
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Controla los eventos que se producen una vez finalizada una actualización de la animación. (Invalida `CUIAnimationTimerEventHandlerBase::OnPostUpdate`).|  
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Controla los eventos que se producen antes de que comience una actualización de la animación. (Invalida `CUIAnimationTimerEventHandlerBase::OnPreUpdate`).|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Controla los eventos que se producen cuando la velocidad de fotogramas de representación de una animación cae por debajo de la velocidad de fotogramas deseable mínimo. (Invalida `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`).|  
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para enrutar eventos.|  
  
## <a name="remarks"></a>Comentarios  
 Este controlador de eventos se crea y se pasa a IUIAnimationTimer::SetTimerEventHandler al llamar a CAnimationController::EnableAnimationTimerEventHandler.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
##  <a name="a-namecreateinstancea--canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationTimerEventHandler::CreateInstance  
 Crea una instancia de devolución de llamada de CAnimationTimerEventHandler.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```  
  
### <a name="parameters"></a>Parámetros  
 `pAnimationController`  
 Un puntero al controlador de animación, que recibe eventos.  
  
 `ppTimerEventHandler`  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se ejecuta correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.  
  
##  <a name="a-nameonpostupdatea--canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>CAnimationTimerEventHandler::OnPostUpdate  
 Controla los eventos que se producen una vez finalizada una actualización de la animación.  
  
```  
IFACEMETHOD(OnPostUpdate)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito; en caso contrario, E_FAIL.  
  
##  <a name="a-nameonpreupdatea--canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>CAnimationTimerEventHandler::OnPreUpdate  
 Controla los eventos que se producen antes de que comience una actualización de la animación.  
  
```  
IFACEMETHOD(OnPreUpdate)();
```  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito; en caso contrario, E_FAIL.  
  
##  <a name="a-nameonrenderingtooslowa--canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>CAnimationTimerEventHandler::OnRenderingTooSlow  
 Controla los eventos que se producen cuando la velocidad de fotogramas de representación de una animación cae por debajo de la velocidad de fotogramas deseable mínimo.  
  
```  
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```  
  
### <a name="parameters"></a>Parámetros  
 `fps`  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito; en caso contrario, E_FAIL.  
  
##  <a name="a-namesetanimationcontrollera--canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController  
 Almacena un puntero al controlador de animación para enrutar eventos.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parámetros  
 `pAnimationController`  
 Un puntero al controlador de animación, que recibe eventos.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

