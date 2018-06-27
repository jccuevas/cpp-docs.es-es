---
title: Clase CD2DPointF | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e23dbce668234fecc3162d52e0bbea6fb05a7b06
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957278"
---
# <a name="cd2dpointf-class"></a>Clase CD2DPointF
Contenedor para `D2D1_POINT_2F`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DPointF : public D2D1_POINT_2F;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Sobrecargado. Construye un `CD2DPointF` objeto `D2D1_POINT_2F` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPointF::operator CPoint](#operator_cpoint)|Convierte `CD2DPointF` a `CPoint` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_POINT_2F`  
  
 `CD2DPointF`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF  
 Construye un objeto CD2DPointF del objeto CPoint.  
  
```  
CD2DPointF(const CPoint& pt);    
CD2DPointF(const D2D1_POINT_2F& pt);    
CD2DPointF(const D2D1_POINT_2F* pt); 
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```  
  
### <a name="parameters"></a>Parámetros  
 *PT*  
 punto de origen  
  
 *fX*  
 origen X  
  
 *fY*  
 origen Y  
  
##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint  
 Convierte CD2DPointF CPoint objeto.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del punto de D2D.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
