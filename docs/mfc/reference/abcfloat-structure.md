---
title: ABCFLOAT (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5be39336f3da839dc9b1c7be6a64db54b59f99bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351620"
---
# <a name="abcfloat-structure"></a>ABCFLOAT (Estructura)
El `ABCFLOAT` estructura contiene los anchos A, B y C de un carácter de la fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _ABCFLOAT { /* abcf */  
    FLOAT abcfA;  
    FLOAT abcfB;  
    FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *abcfA*  
 Especifica el espaciado A del carácter. El espaciado A es la distancia a agregar a la posición actual antes de dibujar el glifo de caracteres.  
  
 *abcfB*  
 Especifica el espaciado B del carácter. El espaciado de B es el ancho de la parte del glifo carácter dibujado.  
  
 *abcfC*  
 Especifica el espaciado de C del carácter. El espaciado de C es la distancia a agregar a la posición actual para proporcionar el espacio en blanco a la derecha del glifo caracteres.  
  
## <a name="remarks"></a>Comentarios  
 Los anchos de A, B y C se miden a lo largo de la línea de base de la fuente. El incremento de carácter (ancho total) de un carácter es la suma de los espacios de A, B y C. El A o el espacio de C puede ser negativo para indicar underhangs o partes sobresalientes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

