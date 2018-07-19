---
title: BITMAPINFO (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9b1bd896157d7f11792a5a6514e30ecd3d46a19
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336262"
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO (Estructura)
La estructura `BITMAPINFO` define las dimensiones y la información de color para un mapa de bits independiente del dispositivo (DIB) de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *bmiHeader*  
 Especifica un [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) estructura que contiene información sobre las dimensiones y el formato de color de un mapa de bits independientes del dispositivo.  
  
 *bmiColors*  
 Especifica una matriz de [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) o tipos de datos DWORD que definen los colores del mapa de bits.  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de bits independiente del dispositivo se compone de dos partes distintas: una estructura `BITMAPINFO` que describe las dimensiones y los colores del mapa de bits y una matriz de bytes que especifica los píxeles del mapa de bits. Los bits de la matriz se empaquetan juntos, pero cada línea de barrido se debe rellenar con ceros para finalizar en un **largo** límite. Si el alto es positivo, el origen del mapa de bits es la esquina inferior izquierda. Si el alto es negativo, el origen es la esquina superior izquierda.  
  
 Un *mapa de bits empaquetado* es un mapa de bits donde la matriz de bytes sigue inmediatamente a la `BITMAPINFO` estructura. Se hace referencia a los mapas de bits empaquetados en un único puntero.  
  
 Para obtener más información sobre la `BITMAPINFO` estructura y los valores adecuados para los miembros de la `BITMAPINFOHEADER` y `RGBQUAD` estructuras, vea los temas siguientes en la documentación del SDK de Windows.  
  
- [BITMAPINFO (estructura)](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) estructura  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) estructura  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

