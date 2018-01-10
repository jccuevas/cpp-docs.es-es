---
title: ABC (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABC
dev_langs: C++
helpviewer_keywords: ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ba8add08fcd5ff3d7343477aafa7d910885b0b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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


