---
title: Desbordamiento de búfer | Documentos de Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13d01460e7ed9cb95d92303d82ea136803737331
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854657"
---
# <a name="buffer-overflow"></a>Desbordamiento de búfer
Varios tamaños de caracteres pueden causar problemas al colocar caracteres en un búfer. Considere el siguiente código, que copia caracteres de una cadena, `sz`, en un búfer, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 ¿La pregunta es: es el último byte copia un byte inicial? A continuación no soluciona el problema porque puede provocar un desbordamiento del búfer:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 El `_mbccpy` llamada intenta hacer lo correcto: copia el carácter completo, ya sea 1 o 2 bytes. Pero esto no tiene en cuenta que el último carácter copiado no podría ajustarse al búfer si el carácter tiene un ancho de 2 bytes. La solución correcta es:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Este código prueba el posible desbordamiento del búfer en el bucle de prueba, con `_mbclen` para probar el tamaño del carácter actual al que apunta `sz`. Mediante la realización de una llamada a la `_mbsnbcpy` función, puede reemplazar el código en el `while` bucle con una sola línea de código. Por ejemplo:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)