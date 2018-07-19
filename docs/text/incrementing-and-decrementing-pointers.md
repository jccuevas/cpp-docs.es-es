---
title: Aumentar y disminuir punteros | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82a6f792ce622481cbbab821b8a5446186bd692d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857134"
---
# <a name="incrementing-and-decrementing-pointers"></a>Aumentar y disminuir punteros
Utilice las siguientes sugerencias:  
  
-   Seleccione bytes iniciales, bytes finales no. Es por lo general no es seguro tiene un puntero a un byte final. Es más seguro buscar una cadena hacia delante en lugar de en orden inverso.  
  
-   Hay funciones de incremento y decremento de puntero y macros que se mueven a través de un carácter completo:  
  
    ```  
    sz1++;  
    ```  
  
     Se convierte en:  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     El `_mbsinc` y `_mbsdec` funciones correctamente aumentar y disminuir en `character` unidades, independientemente del tamaño de carácter.  
  
-   Para las disminuciones, se necesita un puntero en el encabezado de la cadena, como en el siguiente ejemplo:  
  
    ```  
    sz2--;  
    ```  
  
     Se convierte en:  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     Como alternativa, el puntero de encabezado podría ser un carácter válido en la cadena, por ejemplo, que:  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Debe tener un puntero a un byte inicial válidos conocidos.  
  
-   Desea mantener un puntero al carácter anterior para obtener llamadas más rápidas a `_mbsdec`.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)   
 [Índices de byte](../text/byte-indices.md)