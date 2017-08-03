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
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e5d4790cccc280a6a2d23a66c6959fd07bdefa9b
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

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
