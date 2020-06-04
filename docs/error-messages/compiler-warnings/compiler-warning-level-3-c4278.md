---
title: Advertencia del compilador (nivel 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174237"
---
# <a name="compiler-warning-level-3-c4278"></a>Advertencia del compilador (nivel 3) C4278

> '*Identifier*': el identificador de la biblioteca de tipos '*tlb*' ya es una macro; usar el calificador ' Rename '

Cuando se usa [#import](../../preprocessor/hash-import-directive-cpp.md), un identificador de la biblioteca de bibliotecas que se está importando está intentando declarar un *identificador*de identificador. Sin embargo, ya es un símbolo válido.

Use el atributo `#import` **Rename** para asignar un alias al símbolo en la biblioteca de tipos.
