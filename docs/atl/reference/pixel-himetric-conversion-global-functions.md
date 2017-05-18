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
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
caps.latest.revision: 19
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
ms.openlocfilehash: efb7e7da896aea4e377225f4c1e2c9948e635705
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="pixelhimetric-conversion-global-functions"></a>Funciones globales de conversión de píxel/HIMETRIC
Estas funciones proporcionan compatibilidad para la conversión entre píxeles y unidades HIMETRIC.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Unidades HIMETRIC (cada unidad es de 0,01 milímetros) se convierte en píxeles.|  
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
 [out] Puntero al que se devolverá el tamaño del objeto en píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#49;](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

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
 [out] Puntero al que se devolverá el tamaño del objeto en unidades HIMETRIC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM&#51;](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  

## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

