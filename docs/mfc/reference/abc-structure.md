---
title: ABC (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61b5f67247b556b37cdf934f94c30947675533e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="abc-structure"></a>ABC (Estructura)
El **ABC** estructura contiene el ancho de un carácter en una fuente TrueType.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct _ABC { /* abc */  
    int abcA;  
    UINT abcB;  
    int abcC;  
} ABC;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *abcA*  
 Especifica el espaciado A del carácter. El espaciado A es la distancia a agregar a la posición actual antes de dibujar el glifo de caracteres.  
  
 *abcB*  
 Especifica el espaciado B del carácter. El espaciado de B es el ancho de la parte del glifo carácter dibujado.  
  
 *abcC*  
 Especifica el espaciado de C del carácter. El espaciado de C es la distancia a agregar a la posición actual para proporcionar el espacio en blanco a la derecha del glifo caracteres.  
  
## <a name="remarks"></a>Comentarios  
 El ancho total de un carácter es la suma de los espacios de A, B y C. El A o el espacio de C puede ser negativo para indicar underhangs o partes sobresalientes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


