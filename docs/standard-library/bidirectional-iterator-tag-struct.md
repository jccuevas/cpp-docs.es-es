---
title: bidirectional_iterator_tag (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xutility/std::bidirectional_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40eb496203b43f7e71c0ec0b69b561c478e83092
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag (Struct)
Una clase que proporciona un tipo de valor devuelto para la función **iterator_category** que representa un iterador bidireccional.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```  
  
## <a name="remarks"></a>Comentarios  
 Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe buscar la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada tipo de iterador `Iterator`, `iterator_traits`< `Iterator`>:: **iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describe el comportamiento del iterador.  
  
 El tipo es igual a **iterator**\< **Iter**>:: **iterator_category** cuando **Iter** describe un objeto que puede actuar como un iterador bidireccional.  
  
## <a name="example"></a>Ejemplo  
 Vea [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar `bidirectional_iterator_tag`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [forward_iterator_tag (Struct)](../standard-library/forward-iterator-tag-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



