---
title: "Operadores de conversión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a516297b687db349a6bcc867fc94dcd85118a8a5
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="casting-operators"></a>Operadores de conversión
Hay varios operadores de conversión específicos del lenguaje C++. Estos operadores están diseñados para quitar una parte de la ambigüedad y riesgo inherentes a las conversiones antiguas del lenguaje C. Estos operadores son:  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md) usada para la conversión de tipos polimórficos.  
  
-   [static_cast](../cpp/static-cast-operator.md) usada para la conversión de tipos no polimórficos.  
  
-   [const_cast](../cpp/const-cast-operator.md) usa para quitar el `const`, `volatile`, y `__unaligned` atributos.  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md) utilizado para la reinterpretación simple de bits.  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md) se usa para generar MSIL comprobable.  
  
 Use `const_cast` y `reinterpret_cast` como último recurso, ya que estos operadores plantean los mismos peligros que las conversiones antiguas. Sin embargo, siguen siendo necesarios para reemplazar completamente las conversiones antiguas.  
  
## <a name="see-also"></a>Vea también  
 [Conversión](../cpp/casting.md)
