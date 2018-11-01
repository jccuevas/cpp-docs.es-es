---
title: Restricciones de la función main
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555767"
---
# <a name="main-function-restrictions"></a>Restricciones de la función main

Varias restricciones se aplican a la **principal** función que no se aplican a otras funciones de C++. El **principal** función:

- No se pueden sobrecargar (vea [sobrecarga de funciones](function-overloading.md)).

- No se puede declarar como **inline**.

- No se puede declarar como **estático**.

- No se puede tomar su dirección.

- No se puede llamar.

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)