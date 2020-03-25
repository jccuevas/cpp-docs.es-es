---
title: Constantes globales en C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: cabe5e92a496181d60536d7274eca388aba5c068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195479"
---
# <a name="global-constants-in-c"></a>Constantes globales en C++

C++las constantes globales tienen vinculación estática. Es diferente de C. Si intenta usar una constante global en C++ en varios archivos, obtendrá un error externo sin resolver. El compilador optimiza las constantes globales, sin dejar espacio reservado para la variable.

Una manera de resolver este error es incluir las inicializaciones const en un archivo de encabezado e incluir dicho encabezado en los archivos CPP cuando sea necesario, como si fuera un prototipo de función. Otra posibilidad es hacer que la variable no sea constante y usar una referencia constante al evaluarla.

En el ejemplo siguiente se genera C2019:

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

Y luego,

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Consulte también

[Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
