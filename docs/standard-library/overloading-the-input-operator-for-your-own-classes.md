---
title: Sobrecargar el operador &gt;&gt; para las clases propias
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 86b8af963345c8eb9b3f44cfb16332bc09420bf3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624960"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Sobrecargar el operador &gt;&gt; para las clases propias

Los flujos de entrada usan el operador de extracción (`>>`) para los tipos estándar. Puede escribir operadores de extracción similares para sus propios tipos; el éxito depende de usar los espacios en blanco de manera precisa.

Aquí se muestra un ejemplo de un operador de extracción para la clase `Date` que se ha presentado anteriormente:

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)<br/>
