---
title: Sobrecargar el operador &gt;&gt; para las clases propias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d98372009090b0241d9f0190a1d53a9416bbd7ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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
