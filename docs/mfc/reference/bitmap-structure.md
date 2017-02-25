---
title: "BITMAP (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BITMAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BITMAP (estructura)"
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# BITMAP (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura **BITMAP** define el alto, el ancho, el formato de color y los valores de bit de un mapa de bits lógico**.**  
  
## Sintaxis  
  
```  
  
      typedef struct tagBITMAP {  /* bm */  
   int bmType;  
   int bmWidth;  
   int bmHeight;  
   int bmWidthBytes;  
   BYTE bmPlanes;  
   BYTE bmBitsPixel;  
   LPVOID bmBits;  
} BITMAP;  
```  
  
#### Parámetros  
 *bmType*  
 Especifica el tipo de mapa de bits.  Para los mapas de bits lógicos, este miembro debe ser 0.  
  
 *bmWidth*  
 Especifica el ancho del mapa de bits en píxeles.  El ancho debe ser mayor que 0.  
  
 *bmHeight*  
 Especifica el alto del mapa de bits en líneas de trama.  El alto debe ser mayor que 0.  
  
 *bmWidthBytes*  
 Especifica el número de bytes de cada línea de la trama.  Este valor debe ser un número par, ya que la Interfaz de dispositivo gráfico \(GDI\) supone que los valores de bit de un formulario de mapa de bits componen una matriz de valores enteros \(2 bytes\).  Es decir, **bmWidthBytes** \* 8 debe ser el múltiplo siguiente de 16 mayor o igual que el valor obtenido cuando el miembro **bmBitsPixel** se multiplica por el miembro **bmWidth**.  
  
 *bmPlanes*  
 Especifica el número de planos de color del mapa de bits.  
  
 *bmBitsPixel*  
 Especifica el número de bits de color adyacentes en cada plano necesario para definir un píxel.  
  
 *bmBits*  
 Señala a la ubicación de los valores de bits para el mapa de bits.  El miembro **bmBits** debe ser un puntero largo a una matriz de valores de 1 byte.  
  
## Comentarios  
 Los formatos de mapa de bits actualmente utilizados son monocromáticos y en color.  El mapa de bits monocromático utiliza el formato de un 1 bit y 1 plano.  Cada barrido es un múltiplo de 16 bits.  
  
 Los barridos de un mapa de bits monocromático de alto *n* se organizan de la forma siguiente:  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 Los píxeles de un dispositivo monocromático son blanco o negro.  Si el bit correspondiente en el mapa de bits es 1, se activa el píxel \(blanco\).  Si el bit correspondiente en el mapa de bits es 0, se desactiva el píxel \(negro\).  
  
 Todos los dispositivos admiten los mapas de bits que tienen el bit **RC\_BITBLT** establecido en el índice **RASTERCAPS** de la función miembro [CDC::GetDeviceCaps](../Topic/CDC::GetDeviceCaps.md).  
  
 Cada dispositivo tiene su propio formato de color único.  Para transferir un mapa de bits de un dispositivo a otro, utilice las funciones [GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) y [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) de Windows.  
  
## Requisitos  
 **Encabezado:** wingdi.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap::CreateBitmapIndirect](../Topic/CBitmap::CreateBitmapIndirect.md)