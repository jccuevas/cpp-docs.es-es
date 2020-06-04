---
title: Error de las herramientas del vinculador LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990937"
---
# <a name="linker-tools-error-lnk1301"></a>Error de las herramientas del vinculador LNK1301

Módulos CLR de LTCG encontrados, incompatibles con/LTCG: parámetro

Se pasó un módulo compilado con/CLR y/GL al enlazador junto con uno de los parámetros de las optimizaciones guiadas por perfiles (PGO) de/LTCG.

No se admiten las optimizaciones guiadas por perfiles para los módulos/CLR.

Para obtener más información, vea:

- [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Generación de código en tiempo de enlace)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimizaciones guiadas por perfiles](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Para corregir este error

1. No se compila con/CLR o no se vincula con uno de los parámetros de PGO a/LTCG.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK1301:

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
