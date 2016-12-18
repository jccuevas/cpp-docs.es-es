---
title: "Bibliotecas seguras: Biblioteca est&#225;ndar de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_SCL_SECURE_NO_DEPRECATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bibliotecas seguras"
  - "Bibliotecas seguras, Biblioteca estándar de C++"
  - "biblioteca estándar de C++ segura"
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Bibliotecas seguras: Biblioteca est&#225;ndar de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se realizaron varias mejoras a las bibliotecas que se suministran con Visual C\+\+, incluidas la biblioteca estándar de C\+\+, para que sean más seguras.  
  
 Varios métodos de la biblioteca estándar de C\+\+ se han identificado como potencialmente inseguros porque podrían provocar una saturación del búfer u otro defecto de código. El uso de estos métodos no es recomendable. Se crearon nuevos métodos más seguros para reemplazarlos. Todos estos nuevos métodos terminan en `_s`.  
  
 También se realizaron varias mejoras para que los iteradores y los algoritmos sean más seguros. Para obtener más información, vea [Iteradores activados](../standard-library/checked-iterators.md), [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md) y [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md).  
  
## Comentarios  
 En la tabla siguiente se detallan los métodos de la biblioteca estándar de C\+\+ que son potencialmente inseguros, así como sus equivalentes más seguros:  
  
|Método potencialmente inseguro|Equivalente más seguro|  
|------------------------------------|----------------------------|  
|[basic\_string::copy](../Topic/basic_string::copy.md)|[basic\_string::\_Copy\_s](../Topic/basic_string::_Copy_s.md)|  
|[char\_traits::copy](../Topic/char_traits::copy.md)|[char\_traits::\_Copy\_s](../Topic/char_traits::_Copy_s.md)|  
  
 Si se llama a cualquiera de los métodos potencialmente inseguros detallados más arriba, o si usan incorrectamente los iteradores, el compilador generará [Advertencia del compilador \(nivel 3\) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Para obtener información sobre cómo deshabilitar estas advertencias, vea [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
## En esta sección  
 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md)  
  
 [\_SCL\_SECURE\_NO\_WARNINGS](../standard-library/scl-secure-no-warnings.md)  
  
 [Iteradores activados](../standard-library/checked-iterators.md)  
  
 [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)  
  
## Vea también  
 [Información general de STL](../standard-library/cpp-standard-library-overview.md)