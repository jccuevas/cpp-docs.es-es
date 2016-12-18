---
title: "BITMAPINFO (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BITMAPINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BITMAPINFO (estructura)"
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BITMAPINFO (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura `BITMAPINFO` define las dimensiones y la información de color para un mapa de bits independiente del dispositivo \(DIB\) de Windows.  
  
## Sintaxis  
  
```  
typedef struct tagBITMAPINFO {  
   BITMAPINFOHEADER bmiHeader;  
   RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### Parámetros  
 `bmiHeader`  
 Especifica una estructura [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) que contiene información sobre las dimensiones y el formato de color de un mapa de bits independiente del dispositivo.  
  
 `bmiColors`  
 Especifica una matriz de tipos de datos [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) o `DWORD` que definen los colores del mapa de bits.  
  
## Comentarios  
 Un mapa de bits independiente del dispositivo se compone de dos partes distintas: una estructura `BITMAPINFO` que describe las dimensiones y los colores del mapa de bits y una matriz de bytes que especifica los píxeles del mapa de bits.  Los bits de la matriz se empaquetan juntos, pero cada línea de barrido se debe rellenar con ceros para finalizar en un límite `LONG`.  Si el alto es positivo, el origen del mapa de bits es la esquina inferior izquierda.  Si el alto es negativo, el origen es la esquina superior izquierda.  
  
 Un *mapa de bits empaquetado* es un mapa de bits en el que la matriz de bytes sigue inmediatamente a la estructura `BITMAPINFO`.  Se hace referencia a los mapas de bits empaquetados en un único puntero.  
  
 Para obtener más información sobre la estructura `BITMAPINFO` y valores adecuados para los miembros de las estructuras `BITMAPINFOHEADER` y `RGBQUAD`, vea los temas siguientes en la documentación de [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
-   [\<caps:sentence id\="tgt11" sentenceid\="b5dd2e8c9cedbac12eb858bd01a029a2" class\="tgtSentence"\>Estructura BITMAPINFO\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
-   Estructura [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)  
  
-   Estructura [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)