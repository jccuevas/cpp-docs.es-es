---
title: Clase CD2DRectU | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf261f31f470862a506466a8815daef796743f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cd2drectu-class"></a>Clase CD2DRectU
Contenedor para `D2D1_RECT_U`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectU::CD2DRectU](#cd2drectu)|Sobrecargado. Construye un `CD2DRectU` objeto `D2D1_RECT_U` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectU::IsNull](#isnull)|Devuelve un `boolean` valor que indica si una expresión no contiene datos válidos ( `null`).|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRect CD2DRectU::operator](#operator_crect)|Convierte `CD2DRectU` a `CRect` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_RECT_U`  
  
 `CD2DRectU`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="cd2drectu"></a>CD2DRectU::CD2DRectU  
 Construye un objeto CD2DRectU del objeto CRect.  
  
```  
CD2DRectU(const CRect& rect);  
CD2DRectU(const D2D1_RECT_U& rect);  
  CD2DRectU(const D2D1_RECT_U* rect);

 
CD2DRectU(
    UINT32 uLeft = 0,  
    UINT32 uTop = 0,  
    UINT32 uRight = 0,  
    UINT32 uBottom = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 rectángulo de origen  
  
 `uLeft`  
 Coordenada izquierda de origen  
  
 `uTop`  
 Coordenada superior de origen  
  
 `uRight`  
 Coordenada derecha de origen  
  
 `uBottom`  
 Coordenada inferior de origen  
  
##  <a name="isnull"></a>CD2DRectU::IsNull  
 Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la parte superior del rectángulo, izquierda, inferior y derecho valores son iguales a 0; en caso contrario, FALSE.  
  
##  <a name="operator_crect"></a>CRect CD2DRectU::operator  
 Convierte CD2DRectU al objeto CRect.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del rectángulo de D2D.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
