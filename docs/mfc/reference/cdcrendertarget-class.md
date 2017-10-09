---
title: Clase CDCRenderTarget | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: e195979967ac5422be67b634d44e2f5d1afa9263
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="cdcrendertarget-class"></a>Clase CDCRenderTarget
Un contenedor para ID2D1DCRenderTarget.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Construye un objeto CDCRenderTarget.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|Adjunta existente representar la interfaz de destino para el objeto|  
|[CDCRenderTarget::BindDC](#binddc)|Enlaza el destino de representación en el contexto de dispositivo a la que emite los comandos de dibujo|  
|[CDCRenderTarget::Create](#create)|Crea un CDCRenderTarget.|  
|[CDCRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Interfaz de ID2D1DCRenderTarget devuelve|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Interfaz de ID2D1DCRenderTarget devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Un puntero a un objeto ID2D1DCRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="attach"></a>CDCRenderTarget::Attach  
 Adjunta existente representar la interfaz de destino para el objeto  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTarget`  
 Interfaz de destino de representación existente. No puede ser NULL  
  
##  <a name="binddc"></a>CDCRenderTarget::BindDC  
 Enlaza el destino de representación en el contexto de dispositivo a la que emite los comandos de dibujo  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `dc`  
 El contexto de dispositivo para que el destino de representación emite los comandos de dibujo  
  
 `rect`  
 Las dimensiones del identificador de un contexto de dispositivo (HDC) al que está enlazado el destino de representación  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.  
  
##  <a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget  
 Construye un objeto CDCRenderTarget.  
  
```  
CDCRenderTarget();
```  
  
##  <a name="create"></a>CDCRenderTarget::Create  
 Crea un CDCRenderTarget.  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>Parámetros  
 `props`  
 El modo de representación, formato de píxel, opciones de comunicación remota, información de PPP y la compatibilidad de DirectX mínima requerida para la representación de hardware.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.  
  
##  <a name="detach"></a>CDCRenderTarget::Detach  
 Separa la interfaz de destino de representación del objeto  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a desasociar representar la interfaz de destino.  
  
##  <a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget  
 Interfaz de ID2D1DCRenderTarget devuelve  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto todavía no está inicializado.  
  
##  <a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget  
 Un puntero a un objeto ID2D1DCRenderTarget.  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget *  
 Interfaz de ID2D1DCRenderTarget devuelve  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto todavía no está inicializado.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

