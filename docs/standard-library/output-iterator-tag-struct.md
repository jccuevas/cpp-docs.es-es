---
title: output_iterator_tag (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xutility/std::output_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d974e9f9e1b53a6595d8a75e75d6e9bb15dba230
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag (Struct)
Una clase que proporciona un tipo de valor devuelto para una función **iterator_category** que representa un iterador de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
struct output_iterator_tag {};  
  
## <a name="remarks"></a>Comentarios  
 Las clases de etiquetas de categoría se usan como etiquetas de compilación para la selección de algoritmos. La función de plantilla debe buscar la categoría más específica de su argumento de iterador para que pueda usar el algoritmo más eficaz en tiempo de compilación. Para cada iterador de tipo `Iterator`, `iterator_traits`< `Iterator`> **::iterator_category** debe definirse para que sea la etiqueta de categoría más específica que describa el comportamiento del iterador.  
  
 El tipo es igual a **iterator**\< **Iter**> **::iterator_category** cuando **Iter** describe un objeto que puede actuar como un iterador de salida.  
  
 Esta etiqueta no está parametrizada en `value_type` o `difference_type` para el iterador, como con las demás etiquetas de iterador, porque los iteradores de salida no tienen `value_type` ni `difference_type`.  
  
## <a name="example"></a>Ejemplo  
 Vea [iterator_traits](../standard-library/iterator-traits-struct.md) o [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) para obtener un ejemplo de cómo usar **iterator_tag**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



