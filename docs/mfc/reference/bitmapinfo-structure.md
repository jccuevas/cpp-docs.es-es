---
title: Estructura BITMAPINFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9d704fec4a6ae0a95bd393b4a7fffa24884711e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 `bmiHeader`  
 Especifica un [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) estructura que contiene información acerca de las dimensiones y el formato de color de un mapa de bits independiente del dispositivo.  
  
 `bmiColors`  
 Especifica una matriz de [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) o `DWORD` tipos de datos que definen los colores del mapa de bits.  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de bits independiente del dispositivo se compone de dos partes distintas: una estructura `BITMAPINFO` que describe las dimensiones y los colores del mapa de bits y una matriz de bytes que especifica los píxeles del mapa de bits. Los bits de la matriz se empaquetan juntos, pero cada línea de barrido se debe rellenar con ceros para finalizar en un límite `LONG`. Si el alto es positivo, el origen del mapa de bits es la esquina inferior izquierda. Si el alto es negativo, el origen es la esquina superior izquierda.  
  
 A *mapa de bits empaquetado* es un mapa de bits en la matriz de bytes sigue inmediatamente a la `BITMAPINFO` estructura. Se hace referencia a los mapas de bits empaquetados en un único puntero.  
  
 Para obtener más información sobre la `BITMAPINFO` de la estructura y los valores adecuados para los miembros de la `BITMAPINFOHEADER` y `RGBQUAD` estructuras, vea los temas siguientes en la documentación del SDK de Windows.  
  
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

