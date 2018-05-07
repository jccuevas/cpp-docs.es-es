---
title: Clase CBitmapRenderTarget | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd752ff649491ce23b537987ff9f4aebf7811255
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cbitmaprendertarget-class"></a>Clase CBitmapRenderTarget
Un contenedor para ID2D1BitmapRenderTarget.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBitmapRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Construye un objeto CBitmapRenderTarget.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::Attach](#attach)|Adjunta existente representar la interfaz de destino para el objeto|  
|[CBitmapRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|  
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Recupera el mapa de bits para este destino de representación. El mapa de bits devuelto puede utilizarse para las operaciones de dibujo.|  
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Interfaz de ID2D1BitmapRenderTarget devuelve|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|Interfaz de ID2D1BitmapRenderTarget devuelve|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Un puntero a un objeto ID2D1BitmapRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 `CBitmapRenderTarget` 
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="attach"></a>  CBitmapRenderTarget::Attach  
 Adjunta existente representar la interfaz de destino para el objeto  
  
```  
void Attach(ID2D1BitmapRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTarget`  
 Interfaz de destino de representación existente. No puede ser NULL  
  
##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget  
 Construye un objeto CBitmapRenderTarget.  
  
```  
CBitmapRenderTarget();
```  
  
##  <a name="detach"></a>  CBitmapRenderTarget::Detach  
 Separa la interfaz de destino de representación del objeto  
  
```  
ID2D1BitmapRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a desasociar representar la interfaz de destino.  
  
##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap  
 Recupera el mapa de bits para este destino de representación. El mapa de bits devuelto puede utilizarse para las operaciones de dibujo.  
  
```  
BOOL GetBitmap(CD2DBitmap& bitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `bitmap`  
 Cuando este método vuelve, contiene el mapa de bits válida para este destino de representación. Este mapa de bits se puede utilizar para las operaciones de dibujo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.  
  
##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget  
 Interfaz de ID2D1BitmapRenderTarget devuelve  
  
```  
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1BitmapRenderTarget o NULL si el objeto todavía no está inicializado.  
  
##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget  
 Un puntero a un objeto ID2D1BitmapRenderTarget.  
  
```  
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;  
```  
  
##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *  
 Interfaz de ID2D1BitmapRenderTarget devuelve  
  
```  
operator ID2D1BitmapRenderTarget*();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una interfaz ID2D1BitmapRenderTarget o NULL si el objeto todavía no está inicializado.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
