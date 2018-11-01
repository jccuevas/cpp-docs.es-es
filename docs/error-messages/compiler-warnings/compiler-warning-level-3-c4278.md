---
title: Advertencia del compilador (nivel 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627635"
---
# <a name="compiler-warning-level-3-c4278"></a>Advertencia del compilador (nivel 3) C4278

> '*identificador*': identificador de la biblioteca de tipos '*tlb*' ya es una macro; utilice el calificador 'rename'

Cuando se usa [#import](../../preprocessor/hash-import-directive-cpp.md), un identificador de la biblioteca de tipos que va a importar está intentando declarar un identificador *identificador*. Sin embargo, esto ya es un símbolo válido.

Use la `#import` **cambiar el nombre** atributo para asignar un alias al símbolo en la biblioteca de tipos.