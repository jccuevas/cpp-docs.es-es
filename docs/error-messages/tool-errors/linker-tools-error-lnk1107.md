---
title: Error de las herramientas del vinculador LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: 68048d9f824283d002a4ea8b64d88f37bbeefc48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255397"
---
# <a name="linker-tools-error-lnk1107"></a>Error de las herramientas del vinculador LNK1107

archivo no válido o dañado: no se puede leer en la ubicación

La herramienta no pudo leer el archivo. Vuelva a crear el archivo.

LNK1107 también se puede producir si intenta pasar un módulo (extensión de archivo .dll o .netmodule creada con [/CLR: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) o [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)) al vinculador; pase el archivo .obj en su lugar.

Si compila el ejemplo siguiente:

```
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

y, a continuación, especifique **vincular LNK1107.dll** en la línea de comandos, obtendrá LNK1107.  Para resolver el error, especifique **vincular LNK1107.obj** en su lugar.