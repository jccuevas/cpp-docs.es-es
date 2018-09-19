---
title: Las herramientas del vinculador LNK1107 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1107
dev_langs:
- C++
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73a1643d10ea9adc6ac6979eb2de023593ba8d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060712"
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