---
title: "Aritmética de puntero | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 4af0f378f5a89beeb8ce2ccfb4340f0b8538ce36
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="pointer-arithmetic"></a>Aritmética de puntero
Las operaciones de adición que implican un puntero y un entero proporcionan resultados significativos solo si el operando de puntero se dirige a un miembro de matriz y el valor de tipo entero genera un desplazamiento dentro de los límites de la misma matriz. Cuando el valor de tipo entero se convierte en un desplazamiento de dirección, el compilador supone que solo las posiciones de memoria del mismo tamaño quedan entre la dirección original y la dirección más el desplazamiento.  
  
 Esta suposición es válida para los miembros de la matriz. Por definición, una matriz es una serie de valores del mismo tipo; sus elementos residen en ubicaciones de memoria contiguas. Sin embargo, no se garantiza que el almacenamiento de los tipos (excepto de los elementos de matriz) se rellene con el mismo tipo de identificadores. Es decir, los espacios en blanco pueden aparecer entre posiciones de memoria, incluso en posiciones del mismo tipo. Por consiguiente, los resultados de sumar o restar las direcciones de cualquier valor, menos los elementos de matriz, son indefinidos.  
  
 De igual forma, al restar dos valores de puntero, la conversión supone que solo los valores del mismo tipo, sin espacios en blanco, quedan entre las direcciones proporcionadas por los operandos.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de adición de C](../c-language/c-additive-operators.md)
