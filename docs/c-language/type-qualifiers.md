---
title: Calificadores de tipos | Microsoft Docs
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
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
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
ms.openlocfilehash: 491ff4d2b6b1507680f9ad40f73e0055da638204
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="type-qualifiers"></a>Calificadores de tipos
Los calificadores de tipo proporcionan una de dos propiedades a un identificador. El calificador de tipo **const** declara que un objeto no es modificable. El calificador de tipo `volatile` declara un elemento cuyo valor se puede modificar legítimamente por algo que esté más allá del control del programa en el que aparece, por ejemplo, un subproceso que se ejecute en paralelo.  
  
 Los dos calificadores de tipo, **const** y `volatile`, solo pueden aparecer una vez en una declaración. Los calificadores de tipo pueden aparecer con cualquier especificador de tipo; sin embargo, no pueden aparecer después de la primera coma en una declaración de varios elementos. Por ejemplo, las siguientes declaraciones son válidas:  
  
```  
typedef volatile int VI;  
const int ci;  
```  
  
 Estas declaraciones no son válidas:  
  
```  
typedef int *i, volatile *vi;  
float f, const cf;     
```  
  
 Los calificadores de tipo solo son pertinentes al tener acceso a identificadores como valores L en expresiones. Vea [Expresiones de valor L y de valor R](../c-language/l-value-and-r-value-expressions.md) para obtener información sobre valores L y expresiones.  
  
## <a name="syntax"></a>Sintaxis  
 *type-qualifier*:  
 **constvolatile**  
  
 Las siguientes declaraciones **const** y `volatile` son válidas:  
  
```  
int const *p_ci;       /* Pointer to constant int */  
int const (*p_ci);     /* Pointer to constant int */  
int *const cp_i;       /* Constant pointer to int */  
int (*const cp_i);     /* Constant pointer to int */  
int volatile vint;     /* Volatile integer        */  
```  
  
 Si la especificación de un tipo de matriz incluye calificadores de tipo, se califica el elemento, no de tipo de matriz. Si la especificación de tipo de la función incluye calificadores, el comportamiento es indefinido. Ni `volatile` ni **const** afectan al intervalo de valores ni a las propiedades aritméticas del objeto.  
  
 En esta lista se describe cómo usar **const** y `volatile`.  
  
-   La palabra clave **const** se puede usar para modificar cualquier tipo fundamental o agregado, un puntero a un objeto de cualquier tipo o `typedef`. Si un elemento se declara solo con el calificador de tipo **const**, se asume que su tipo es **const int**. Una variable **const** se puede inicializar o puede colocarse en un área de almacenamiento de solo lectura. La palabra clave **const** es útil para declarar punteros a **const** puesto que requiere que la función no cambie el puntero de ninguna manera.  
  
-   El compilador supone que, en cualquier punto del programa, se puede tener acceso a una variable `volatile` mediante un proceso desconocido que utilice o modifique su valor. Por consiguiente, independientemente de las optimizaciones especificadas en la línea de comandos, el código de cada asignación de una variable `volatile` y cada referencia a la misma debe generarse aunque no parezca surtir ningún efecto.  
  
     Si solo se usa `volatile`, se supone `int`. El especificador de tipo `volatile` se puede utilizar para proporcionar acceso confiable a ubicaciones de memoria especiales. Use `volatile` con objetos de datos a los que se pueda tener acceso o que se puedan modificar mediante controladores de la señal, ejecutando programas simultáneamente o mediante hardware especial tal como registros de control de E/S asignados a la memoria. Puede declarar una variable como `volatile` mientras dure o puede convertir una única referencia para que sea `volatile`.  
  
-   Un elemento puede ser a la vez **const** y `volatile`, en cuyo caso el elemento no se podría modificar de manera legítima por su propio programa, pero podría modificarlo algún proceso asincrónico.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)
