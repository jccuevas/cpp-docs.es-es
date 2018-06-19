---
title: Clase CD2DPointU | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91496e96763ab8c79ae1c71d68b9ae8f8db15e50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350561"
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
  
##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU  
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
  
##  <a name="operator_cpoint"></a>  CD2DPointU::operator CPoint  
 Convierte CD2DPointU CPoint objeto.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Valor devuelto  
 Valor actual del punto de D2D.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)
