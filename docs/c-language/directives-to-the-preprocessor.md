---
title: Directivas para el preprocesador
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149042"
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
