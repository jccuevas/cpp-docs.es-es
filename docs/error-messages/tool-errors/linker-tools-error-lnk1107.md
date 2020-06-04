---
title: Error de las herramientas del vinculador LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: c75966d9c6c22f1bd2123fb30282bb2bed467130
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991030"
---
# <a name="linker-tools-error-lnk1107"></a>Error de las herramientas del vinculador LNK1107

archivo no válido o dañado: no se puede leer en la ubicación

La herramienta no pudo leer el archivo. Vuelva a crear el archivo.

LNK1107 también podría producirse si intenta pasar un módulo (extensión. dll o. netmodule creada con [/clr: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) o [/noAssembly](../../build/reference/noassembly-create-a-msil-module.md)) al enlazador. Pase el archivo. obj en su lugar.

Si compila el ejemplo siguiente:

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

y después especifique **Link LNK1107. dll** en la línea de comandos, obtendrá LNK1107.  Para resolver el error, especifique en su lugar **Link LNK1107. obj** .
