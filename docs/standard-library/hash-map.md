---
title: "&lt;hash_map&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<hash_map>"
  - "<hash_map>"
  - "std::<hash_map>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map (encabezado)"
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# &lt;hash_map&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este encabezado está obsoleto. La alternativa es [\<unordered\_map\>](../standard-library/unordered-map.md).  
  
 Define las clases de plantilla de contenedor hash\_map y hash\_multimap y sus plantillas auxiliares.  
  
 En Visual C\+\+ .NET 2003, los miembros de los archivos de encabezado [\<hash\_map\>](#vclrfhash_map_header_file) y [\<hash\_set\>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext. Vea [stdext \(Espacio de nombres\)](../standard-library/stdext-namespace.md) para obtener más información.  
  
## Sintaxis  
  
```  
  
#include <hash_map>  
  
```  
  
### Operadores  
  
|Versión de hash\_map|Versión de hash\_multimap|Descripción|  
|--------------------------|-------------------------------|-----------------|  
|[operator\!\= \(hash\_map\)](../Topic/operator!=%20\(hash_map\).md)|[operator\!\= \(hash\_multimap\)](../Topic/operator!=%20\(hash_multimap\).md)|Comprueba si el objeto hash\_map o hash\_multimap del lado izquierdo del operador no es igual al objeto hash\_map o hash\_multimap del lado derecho.|  
|[operator\=\= \(hash\_map\)](http://msdn.microsoft.com/es-es/f933cb1c-934d-43f5-aa9e-0b325eb95b85)|[operator\=\= \(hash\_multimap\)](http://msdn.microsoft.com/es-es/3fa378b1-0250-4e3f-a130-dc14103fc5e9)|Comprueba si el objeto hash\_map o hash\_multimap del lado izquierdo del operador es igual al objeto hash\_map o hash\_multimap del lado derecho.|  
  
### Funciones de plantilla especializadas  
  
|Versión de hash\_map|Versión de hash\_multimap|Descripción|  
|--------------------------|-------------------------------|-----------------|  
|[swap \(hash\_map\)](../Topic/hash_map::swap.md)|[swap \(hash\_multimap\)](../Topic/hash_multimap::swap.md)|Intercambia los elementos de dos encabezados hash\_map o hash\_multimap.|  
  
### Clases  
  
|||  
|-|-|  
|[hash\_compare \(Clase\)](../standard-library/hash-compare-class.md)|Describe un objeto que se puede usar con cualquiera de los contenedores asociativos hash \(hash\_map, hash\_multimap, hash\_set o hash\_multiset\) como objeto de parámetro **Traits** predeterminado para ordenar y aplicar algoritmos hash a los elementos que contienen.|  
|[value\_compare \(Clase\)](../standard-library/value-compare-class.md)|Proporciona un objeto de función que puede comparar los elementos de hash\_map al comparar los valores de sus claves para determinar su orden relativo en hash\_map.|  
|[hash\_map \(Clase\)](../standard-library/hash-map-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor es único y un valor de datos asociado.|  
|[hash\_multimap \(Clase\)](../standard-library/hash-multimap-class.md)|Se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor no necesita ser único y un valor de datos asociado.|  
  
## Requisitos  
 **Encabezado:** \<hash\_map\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)