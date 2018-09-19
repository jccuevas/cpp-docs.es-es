---
title: Desbordamiento de búfer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11a3da883dae4d292a55eb2537fd98609404b5a9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609517"
---
# <a name="buffer-overflow"></a>Desbordamiento de búfer
Varios tamaños de caracteres pueden causar problemas cuando se coloca en un búfer de caracteres. Considere el siguiente código, que copia los caracteres de una cadena, `sz`, en un búfer, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 ¿La pregunta es: es el último byte copia un byte inicial? El siguiente no soluciona el problema porque puede provocar un desbordamiento del búfer:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 El `_mbccpy` llamada intenta hacer lo correcto, copie el carácter completo, ya sea 1 o 2 bytes. Pero esto no tiene en cuenta que el último carácter copiado no podría ajustarse al búfer si el carácter tiene un ancho de 2 bytes. La solución correcta es:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Este código comprueba posible desbordamiento del búfer en el bucle de prueba, mediante `_mbclen` para probar el tamaño del carácter actual apuntado `sz`. Mediante una llamada a la `_mbsnbcpy` función, puede reemplazar el código en el **mientras** bucle con una sola línea de código. Por ejemplo:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)