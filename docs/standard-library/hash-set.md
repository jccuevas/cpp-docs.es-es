---
title: "&lt;hash_set&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<hash_set>"
  - "std.<hash_set>"
  - "std::<hash_set>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_set (encabezado)"
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;hash_set&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Este encabezado está obsoleto. La alternativa es [\<unordered\_set\>](../standard-library/unordered-set.md).  
  
 Define las clases de plantilla de contenedor hash\_set y hash\_multiset, así como sus plantillas auxiliares.  
  
## Sintaxis  
  
```  
  
#include <hash_set>  
  
```  
  
## Comentarios  
 En Visual C\+\+ .NET 2003, los miembros de los archivos de encabezado [\<hash\_map\>](../standard-library/hash-map.md) y [\<hash\_set\>](#vclrfhash_set_header_file) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext. Vea [El espacio de nombres stdext](../standard-library/stdext-namespace.md) para obtener más información.  
  
### Operadores  
  
|Hash\_set \(versión\)|Hash\_multiset \(versión\)|Descripción|  
|---------------------------|--------------------------------|-----------------|  
|[operator\!\= \(hash\_set\)](../Topic/operator!=%20\(hash_set\).md)|[operator\!\= \(hash\_multiset\)](../Topic/operator!=%20\(hash_multiset\).md)|Comprueba si el objeto hash\_set o hash\_multiset situado a la izquierda del operador no es igual que el objeto hash\_set o hash\_multiset situado a la derecha.|  
|[operator\=\= \(hash\_set\)](http://msdn.microsoft.com/es-es/791b95bd-f917-4716-aea6-add50badbfac)|[operator\=\= \(hash\_multiset\)](http://msdn.microsoft.com/es-es/cfa9aa0c-d5f6-403a-9441-35c2a4cee0fb)|Comprueba si el objeto hash\_set o hash\_multiset situado a la izquierda del operador es igual que el objeto hash\_set o hash\_multiset situado a la derecha.|  
  
### Funciones de plantilla especializadas  
  
|Hash\_set \(versión\)|Hash\_multiset \(versión\)|Descripción|  
|---------------------------|--------------------------------|-----------------|  
|[swap \(hash\_set\)](../Topic/swap%20\(hash_set\).md)|[swap \(hash\_multiset\)](../Topic/swap%20\(hash_multiset\).md)|Intercambia los elementos de dos encabezados hash\_sets o hash\_multisets.|  
  
### Clases  
  
|||  
|-|-|  
|[hash\_compare \(Clase\)](../standard-library/hash-compare-class.md)|Describe un objeto que se puede usar con cualquiera de los contenedores asociativos hash \(hash\_map, hash\_multimap, hash\_set o hash\_multiset\) como objeto de parámetro **Traits** predeterminado para ordenar y aplicar algoritmos hash a los elementos que contienen.|  
|[hash\_set \(Clase\)](../standard-library/hash-set-class.md)|Se usa para el almacenamiento y la recuperación de datos rápida de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave.|  
|[hash\_multiset \(Clase\)](../standard-library/hash-multiset-class.md)|Se usa para el almacenamiento y la recuperación de datos rápida de una colección en la que los valores de los elementos contenidos son únicos y sirven como valores de clave.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)