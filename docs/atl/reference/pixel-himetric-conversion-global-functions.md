---
title: "Funciones globales de conversión de píxel HIMETRIC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d670d667345c233fc499cda42194dfafa185dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pixelhimetric-conversion-global-functions"></a>Funciones globales de conversión de píxel/HIMETRIC
Estas funciones proporcionan compatibilidad para la conversión entre píxeles y unidades HIMETRIC.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Convierte unidades HIMETRIC (cada unidad es de 0,01 milímetros) en píxeles.|  
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Convierte los píxeles en unidades HIMETRIC (cada unidad es de 0,01 milímetros).|  
  
##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel  
 Convierte un tamaño de objeto en unidades HIMETRIC (cada unidad es de 0,01 milímetros) a un tamaño en píxeles del dispositivo de pantalla.  
  
 
```
extern void AtlHiMetricToPixel(
  const SIZEL* lpSizeInHiMetric, 
  LPSIZEL lpSizeInPix);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSizeInHiMetric`  
 [in] Puntero al tamaño del objeto en unidades HIMETRIC.  
  
 `lpSizeInPix`  
 [out] Puntero a donde se devolverá el tamaño del objeto en píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric  
 Convierte un tamaño de objeto especificado en píxeles en el dispositivo de pantalla en un tamaño especificado en unidades HIMETRIC (cada unidad es de 0,01 milímetros).  
  
```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix, 
    LPSIZEL lpSizeInHiMetric);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpSizeInPix`  
 [in] Puntero al tamaño del objeto en píxeles.  
  
 `lpSizeInHiMetric`  
 [out] Puntero a la ubicación el tamaño del objeto en unidades HIMETRIC va a devolver.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)
