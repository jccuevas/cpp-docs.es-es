---
title: Literales de cadena en expresiones primarias | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, in primary expressions
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 818284a0eabce779d9f52e8fe7b3af4cc1d8df4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095534"
---
# <a name="string-literals-in-primary-expressions"></a>Literales de cadena en expresiones primarias

Un “literal de cadena” es un carácter, un carácter ancho o una secuencia de caracteres consecutivos incluidos entre comillas dobles. Puesto que no son variables, los literales de cadena ni ninguno de sus elementos pueden ser el operando izquierdo de una operación de asignación. El tipo de un literal de cadena es una matriz de `char` (o una matriz de `wchar_t` para literales de cadena anchos). Las matrices incluidas en expresiones se convierten en punteros. Para más información sobre las cadenas, vea [Literales de cadena](../c-language/c-string-literals.md).

## <a name="see-also"></a>Vea también

[Expresiones primarias de C](../c-language/c-primary-expressions.md)