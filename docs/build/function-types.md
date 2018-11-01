---
title: Tipos de funciones
ms.date: 11/04/2016
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
ms.openlocfilehash: 22778f3eaefa6dbcf5f85e54c0940867ef52ab72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526411"
---
# <a name="function-types"></a>Tipos de funciones

Básicamente hay dos tipos de funciones. Una función que requiere un marco de pila se invoca una función de marco. Una función que no requiere un marco de pila se invoca una función de hoja.

Una función de marco es una función que asigna espacio de pila, llama a otras funciones, guarda los registros no volátiles o usa el control de excepciones. También requiere una entrada de la tabla de función. Una función de marco requiere un prólogo y un epílogo. Una función de marco puede asignar dinámicamente el espacio de pila y puede emplear un puntero de marco. Una función de marco tiene todas las capacidades de este estándar de llamada a su disposición.

Si una función de marco no llama a otra función, no es necesario para alinear la pila (al que hace referencia en la sección [asignación de pila](../build/stack-allocation.md)).

Una función de hoja es aquella que no requiere una entrada de la tabla de función. No puede realizar cambios en los registros no volátiles, incluidos RSP, lo que significa que no se puede llamar a las funciones o asignar espacio de pila. Puede dejar la pila sin alinear mientras ejecuta.

## <a name="see-also"></a>Vea también

[Uso de las pilas](../build/stack-usage.md)
