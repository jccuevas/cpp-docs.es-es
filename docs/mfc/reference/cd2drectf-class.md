---
title: Clase CD2DRectF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f96adf519eb710d412465a9db4cbd7313f91f41
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338277"
---
# <a name="cd2drectf-class"></a>Clase CD2DRectF
Contenedor para `D2D1_RECT_F`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](#cd2drectf)|Sobrecargado. Construye un `CD2DRectF` objeto `D2D1_RECT_F` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|Devuelve un **booleano** valor que indica si una expresión no contiene datos válidos (NULL).|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRect CD2DRectF::operator](#operator_crect)|Convierte `CD2DRectF` a `CRect` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF  
 Construye un objeto CD2DRectF del objeto CRect.  
  
```  
CD2DRectF(const CRect& rect);  
CD2DRectF(const D2D1_RECT_F& rect);  
  CD2DRectF(const D2D1_RECT_F* rect);

 
CD2DRectF(
    FLOAT fLeft = 0.,  
    FLOAT fTop = 0.,  
    FLOAT fRight = 0.,  
    FLOAT fBottom = 0.);
```  
  
### <a name="parameters"></a>Parámetros  
 *Rect*  
 rectángulo de origen  
  
 *fLeft*  
 Coordenada izquierda de origen  
  
 *fTop*  
 Coordenada superior de origen  
  
 *Más*  
 Coordenada derecha de origen  
  
 *fBottom*  
 Coordenada inferior de origen  
  
##  <a name="isnull"></a>  CD2DRectF::IsNull  
 Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si son iguales a 0; superior, izquierdo, inferior y valores correctos del rectángulo en caso contrario, FALSE.  
  
##  <a name="operator_crect"></a>  CRect CD2DRectF::operator  
 Convierte CD2DRectF objeto CRect.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del rectángulo de D2D.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
