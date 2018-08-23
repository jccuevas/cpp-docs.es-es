---
title: Asignación de caracteres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5efdaefdfd961a10d40c00855261eb547164f95
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591406"
---
# <a name="character-assignment"></a>Asignación de caracteres
Considere el ejemplo siguiente, en el que el **mientras** bucle busca una cadena y copia todos los caracteres excepto 'X' en otra cadena:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
        *sz1++ = *sz2++;  
    else  
        sz2++;  
}  
```  
  
 El código copia el byte de `sz2` a la ubicación señalada por `sz1`, a continuación, incrementa `sz1` para recibir el siguiente byte. Pero si el carácter siguiente en `sz2` es un carácter de doble byte, la asignación a `sz1` copia solo el primer byte. El código siguiente utiliza una función portátil para copiar el carácter de forma segura y otra para incrementar `sz1` y `sz2` correctamente:  
  
```  
while( *sz2 )  
{  
    if( *sz2 != 'X' )  
    {  
        _mbscpy_s( sz1, 1, sz2 );  
        sz1 = _mbsinc( sz1 );  
        sz2 = _mbsinc( sz2 );  
    }  
    else  
        sz2 = _mbsinc( sz2 );  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)   
 [Comparación de caracteres](../text/character-comparison.md)