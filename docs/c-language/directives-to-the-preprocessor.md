---
title: Directivas para el preprocesador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1ddecf1e205cc9a6d7f09a27fbf243417540e49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033568"
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