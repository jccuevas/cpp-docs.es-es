---
title: Restricciones de la función Main | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93f5cce15d4db9f7f6d4e3361d22028fccd676f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117366"
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