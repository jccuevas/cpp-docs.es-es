---
title: ABC (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: 11
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: c8b49cd8a94c5ff580393814be08b1819a1eca52
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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
 Especifica el espaciado entre un carácter. El espaciado A es la distancia para agregar a la posición actual antes de dibujar el glifo de caracteres.  
  
 *abcB*  
 Especifica el espaciado B del carácter. El espaciado de B es el ancho de la parte del glifo carácter dibujado.  
  
 *abcC*  
 Especifica el espaciado de C del carácter. El espaciado de C es la distancia para agregar a la posición actual para proporcionar el espacio en blanco a la derecha del glifo del carácter.  
  
## <a name="remarks"></a>Comentarios  
 El ancho total de un carácter es la suma de los espacios A, B y C. El o el espacio de C puede ser negativo para indicar underhangs o partes sobresalientes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** wingdi.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)



