---
title: Directivas para el preprocesador
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 0abc21f38f5776acd9167f0526160dc5e1bb8cbb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450076"
---
# <a name="directives-to-the-preprocessor"></a>Directivas para el preprocesador

Una “directiva” indica al preprocesador de C que realice una acción concreta en el texto del programa antes de la compilación. Las [directivas de preprocesador](../preprocessor/preprocessor-directives.md) se describen con detalle en la *referencia del preprocesador*. En el ejemplo siguiente se usa la directiva de preprocesador `#define`:

```
#define MAX 100
```

Esta instrucción indica al compilador que reemplace cada aparición de `MAX` por `100` antes de la compilación. Las directivas de preprocesador del compilador de C son:

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>Vea también

[Archivos de código fuente y programas origen](../c-language/source-files-and-source-programs.md)