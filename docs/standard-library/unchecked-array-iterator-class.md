---
title: "unchecked_array_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unchecked_array_iterator"
  - "stdext::unchecked_array_iterator"
dev_langs: 
  - "C++"
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# unchecked_array_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase `unchecked_array_iterator` permite ajustar una matriz o un puntero en un iterador no comprobado.  Use esta clase como contenedor \(mediante la función [make\_unchecked\_array\_iterator](../Topic/make_unchecked_array_iterator.md)\) para punteros o matrices sin formato como una manera dirigida de administrar advertencias de puntero no comprobadas en lugar de silenciar de manera global estas advertencias.  Si es posible, use la versión comprobada de esta clase, [checked\_array\_iterator](../standard-library/checked-array-iterator-class.md).  
  
> [!NOTE]
>  Esta clase es una extensión de Microsoft de la Biblioteca estándar de C\+\+.  El código implementado mediante esta función no es portable a los entornos de compilación estándar de C\+\+ que no admiten esta extensión de Microsoft.  
  
## Sintaxis  
  
```  
template <class Iterator>  
    class unchecked_array_iterator;  
```  
  
## Comentarios  
 Esta clase se define en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).  
  
 Esta es la versión no comprobada de la [clase checked\_array\_iterator](../standard-library/checked-array-iterator-class.md) y admite las mismas sobrecargas y los mismos miembros.  Para obtener más información sobre la característica de iterador comprobado con ejemplos de código, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)