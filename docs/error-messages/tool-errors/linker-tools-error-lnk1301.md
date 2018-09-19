---
title: Las herramientas del vinculador LNK1301 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8646de5bb81120f6445e16b819b27da62ed9d5ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039951"
---
# <a name="linker-tools-error-lnk1301"></a>Error de las herramientas del vinculador LNK1301

Módulos clr LTCG encontrados incompatibles con/LTCG: parámetro

Un módulo compilado con/CLR y/GL se pasó al vinculador junto con una de las optimizaciones guiadas por perfiles parámetros (PGO) de/LTCG.

Las optimizaciones guiadas por perfiles no se admiten para los módulos / CLR.

Para obtener más información, consulte:

- [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Generación de código en tiempo de enlace)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Para corregir este error

1. No compila con/CLR o no vincula con uno de los parámetros PGO a/LTCG.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK1301:

```
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```