---
title: forward_iterator_tag (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.forward_iterator_tag
- forward_iterator_tag
- std::forward_iterator_tag
- xutility/std::forward_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 659ada41e69a0d9d2ab90e80b60ea0b3e4546d3b
ms.lasthandoff: 02/24/2017

---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag (Struct)
Clase que proporciona un tipo de valor devuelto para una función **iterator_category** que representa un iterador hacia delante.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct forward_iterator_tag    : public input_iterator_tag {};
```  
  
## <a name="remarks"></a>Comentarios  
 Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe descubrir cuál es la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada iterador de tipo `Iterator`, `iterator_traits`< `Iterator`> **::iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describa el comportamiento del iterador.  
  
 El tipo es igual a **iterator**\< **Iter**> **::iterator_category** cuando **Iter** describe un objeto que puede actuar como un iterador hacia delante.  
  
## <a name="example"></a>Ejemplo  
 Vea [iterator_traits](../standard-library/iterator-traits-struct.md) o [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar **iterator_tag**s.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [input_iterator_tag (Struct)](../standard-library/input-iterator-tag-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




