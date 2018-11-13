---
title: Aritmética de puntero
ms.date: 11/04/2016
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
ms.openlocfilehash: 7ed238bdeedf95bb79543a28ed8dd602020fa55b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615480"
---
# <a name="pointer-arithmetic"></a>Aritmética de puntero

Las operaciones de adición que implican un puntero y un entero proporcionan resultados significativos solo si el operando de puntero se dirige a un miembro de matriz y el valor de tipo entero genera un desplazamiento dentro de los límites de la misma matriz. Cuando el valor de tipo entero se convierte en un desplazamiento de dirección, el compilador supone que solo las posiciones de memoria del mismo tamaño quedan entre la dirección original y la dirección más el desplazamiento.

Esta suposición es válida para los miembros de la matriz. Por definición, una matriz es una serie de valores del mismo tipo; sus elementos residen en ubicaciones de memoria contiguas. Sin embargo, no se garantiza que el almacenamiento de los tipos (excepto de los elementos de matriz) se rellene con el mismo tipo de identificadores. Es decir, los espacios en blanco pueden aparecer entre posiciones de memoria, incluso en posiciones del mismo tipo. Por consiguiente, los resultados de sumar o restar las direcciones de cualquier valor, menos los elementos de matriz, son indefinidos.

De igual forma, al restar dos valores de puntero, la conversión supone que solo los valores del mismo tipo, sin espacios en blanco, quedan entre las direcciones proporcionadas por los operandos.

## <a name="see-also"></a>Vea también

[Operadores de adición de C](../c-language/c-additive-operators.md)