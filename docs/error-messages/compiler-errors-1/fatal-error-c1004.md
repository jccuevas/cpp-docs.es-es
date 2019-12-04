---
title: Error irrecuperable C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756973"
---
# <a name="fatal-error-c1004"></a>Error irrecuperable C1004

se encontró un final de archivo inesperado

El compilador llegó al final de un archivo de código fuente sin resolver una construcción. Puede que falte el código de uno de los siguientes elementos:

- Una llave de cierre

- Un paréntesis de cierre

- Un marcador de comentario de cierre (*/)

- Un punto y coma

Para resolver este error, compruebe lo siguiente:

- La unidad de disco predeterminada no tiene suficiente espacio para los archivos temporales, que requieren aproximadamente el doble de espacio que el archivo de código fuente.

- Una directiva de `#if` que se evalúa como false carece de una directiva de cierre `#endif`.

- Un archivo de código fuente no termina con un retorno de carro y avance de línea.

En el ejemplo siguiente se genera C1004:

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

Solución posible:

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
