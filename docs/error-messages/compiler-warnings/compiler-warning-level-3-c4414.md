---
title: Compilador advertencia (nivel 3) C4414 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1526b20732d7a1b08ec8d753cb64e33e42dd809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289713"
---
# <a name="compiler-warning-level-3-c4414"></a>Advertencia del compilador (nivel 3) C4414
'función': salto short a la función ha convertido en near  
  
 Los saltos short generan una instrucción compacta que se bifurca a una dirección dentro de un intervalo limitado de la instrucción. La instrucción incluye un desplazamiento short que representa la distancia entre el salto y la dirección de destino, la definición de función. Durante la vinculación, una función puede mover o someter a optimizaciones en tiempo de vínculo que consiguen que la función puede moverse fuera del intervalo alcanzable desde un desplazamiento short. El compilador debe generar un registro especial para el salto, que requiere que la instrucción jmp sea NEAR o FAR. El compilador realiza la conversión.  
  
 Por ejemplo, el código siguiente genera C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```