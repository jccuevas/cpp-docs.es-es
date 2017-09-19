---
title: Clase CD2DRectF | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF class
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5bca2dcce32679083e5917d855f711984989a489
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cd2drectf-class"></a>Clase CD2DRectF
Contenedor para `D2D1_RECT_F`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](#cd2drectf)|Sobrecargado. Construye un `CD2DRectF` objeto `D2D1_RECT_F` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|Devuelve un `boolean` valor que indica si una expresión no contiene datos válidos ( `null`).|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRect CD2DRectF::operator](#operator_crect)|Convierte `CD2DRectF` a `CRect` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>CD2DRectF::CD2DRectF  
 Construye un objeto CD2DRectF de objeto CRect.  
  
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
 `rect`  
 rectángulo de origen  
  
 `fLeft`  
 Coordenada izquierda de origen  
  
 `fTop`  
 Coordenada superior de origen  
  
 `fRight`  
 Coordenada derecha de origen  
  
 `fBottom`  
 Coordenada inferior de origen  
  
##  <a name="isnull"></a>CD2DRectF::IsNull  
 Devuelve un valor booleano que indica si una expresión no contiene datos válidos (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la parte superior del rectángulo, izquierda, inferior y derecho valores son iguales a 0; de lo contrario, FALSE.  
  
##  <a name="operator_crect"></a>CRect CD2DRectF::operator  
 Convierte CD2DRectF al objeto CRect.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del rectángulo de D2D.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

