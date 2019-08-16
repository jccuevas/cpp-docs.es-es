---
title: Restricciones de la función main
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301843"
---
# <a name="main-function-restrictions"></a>Restricciones de la función main

Varias restricciones se aplican a la **principal** función que no se aplican a otras funciones de C++. El **principal** función:

- No se pueden sobrecargar (vea [sobrecarga de funciones](function-overloading.md)).

- No se puede declarar como **inline**.

- No se puede declarar como **estático**.

- No se puede tomar su dirección.

- No se puede llamar.

## <a name="see-also"></a>Vea también

[main: inicio de programa](../cpp/main-program-startup.md)