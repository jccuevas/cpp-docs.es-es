---
title: Directivas para el preprocesador | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 764bfd086612a10076e5c4800768b7b850ddbc7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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