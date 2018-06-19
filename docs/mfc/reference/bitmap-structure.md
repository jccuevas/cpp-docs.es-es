---
title: Estructura de mapa de bits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa8bb4ab914b4e05eb21cfc45a243328d32bb6d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351642"
---
# <a name="bitmap-structure"></a>BITMAP (Estructura)
El **mapa de bits** estructura define el alto, ancho, formato de color y valores de bit de un mapa de bits lógico **.**  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 *bmType*  
 Especifica el tipo de mapa de bits. Para los mapas de bits lógicos, este miembro debe ser 0.  
  
 *Bmbitspixel*  
 Especifica el ancho del mapa de bits en píxeles. El ancho debe ser mayor que 0.  
  
 *bmHeight*  
 Especifica el alto del mapa de bits en líneas de trama. El alto debe ser mayor que 0.  
  
 *bmWidthBytes*  
 Especifica el número de bytes de cada línea de la trama. Este valor debe ser un número par, ya que la Interfaz de dispositivo gráfico (GDI) supone que los valores de bit de un formulario de mapa de bits componen una matriz de valores enteros (2 bytes). En otras palabras, **bmWidthBytes** \* 8 debe ser el múltiplo siguiente de 16 mayor o igual que el valor obtenido cuando el **Bmbitspixel** miembro se multiplica por el **Bmwidth**  miembro.  
  
 *bmPlanes*  
 Especifica el número de planos de color del mapa de bits.  
  
 *Bmwidth*  
 Especifica el número de bits de color adyacentes en cada plano necesario para definir un píxel.  
  
 *bmBits*  
 Señala a la ubicación de los valores de bits para el mapa de bits. El **bmBits** miembro debe ser un puntero largo a una matriz de valores de 1 byte.  
  
## <a name="remarks"></a>Comentarios  
 Los formatos de mapa de bits actualmente utilizados son monocromáticos y en color. El mapa de bits monocromático utiliza el formato de un 1 bit y 1 plano. Cada barrido es un múltiplo de 16 bits.  
  
 Exámenes se organizan del siguiente modo para un mapa de bits monocromático de alto *n*:  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 Los píxeles de un dispositivo monocromático son blanco o negro. Si el bit correspondiente en el mapa de bits es 1, se activa el píxel (blanco). Si el bit correspondiente en el mapa de bits es 0, se desactiva el píxel (negro).  
  
 Todos los dispositivos admiten los mapas de bits que tienen la **RC_BITBLT** bit establecido en el **RASTERCAPS** índice de la [CDC:: GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps) función miembro.  
  
 Cada dispositivo tiene su propio formato de color único. Para transferir un mapa de bits de un dispositivo a otro, utilice el [GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879) y [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) funciones de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
