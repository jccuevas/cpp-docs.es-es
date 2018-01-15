---
title: Clase CD2DPointU | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
dev_langs: C++
helpviewer_keywords: CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5af7ab3327a7c3d2f1afc31ad8cc2bde144eeb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpointu-class"></a>Clase CD2DPointU
Contenedor para `D2D1_POINT_2U`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CD2DPointU : public D2D1_POINT_2U;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Sobrecargado. Construye un `CD2DPointU` del objeto `D2D1_POINT_2U` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPointU::operator CPoint](#operator_cpoint)|Convierte `CD2DPointU` a `CPoint` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `D2D1_POINT_2U`  
  
 `CD2DPointU`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrendertarget.h  
  
##  <a name="cd2dpointu"></a>CD2DPointU::CD2DPointU  
 Construye un objeto CD2DPointU del objeto CPoint.  
  
```  
CD2DPointU(const CPoint& pt);  
CD2DPointU(const D2D1_POINT_2U& pt);  
  CD2DPointU(const D2D1_POINT_2U* pt);  
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 punto de origen  
  
 `uX`  
 origen X  
  
 `uY`  
 origen Y  
  
##  <a name="operator_cpoint"></a>CD2DPointU::operator CPoint  
 Convierte CD2DPointU CPoint objeto.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del punto de D2D.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
