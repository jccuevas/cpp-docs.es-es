---
title: Constantes globales en C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 3da61b7718dadba9b454ee079651ce6372f21756
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432622"
---
# <a name="global-constants-in-c"></a>Constantes globales en C++

Constantes globales de C++ tienen vinculación estática. Esto es diferente de C. Si intenta usar un global constante en C++ en varios archivos obtendrá un error externo sin resolver. El compilador optimiza constantes globales, sin dejar espacio reservado para la variable.

Una manera de resolver este error consiste en incluir las inicializaciones constantes en un archivo de encabezado e incluir dicho encabezado en los archivos CPP cuando sea necesario, como si fuera un prototipo de función. Otra posibilidad es hacer que la variable no constante y utilizar una referencia constante al evaluarla.

El ejemplo siguiente genera C2019:

```
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

Y luego,

```
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Vea también

[Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)