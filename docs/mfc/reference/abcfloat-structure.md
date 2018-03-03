---
title: ABCFLOAT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b58871df5a526455297dd6d092f98e9facd901ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

