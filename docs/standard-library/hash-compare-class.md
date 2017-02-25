---
title: "hash_compare (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hash_set/stdext::hash_compare"
  - "std.hash_compare"
  - "hash_compare"
  - "std::hash_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_compare (clase)"
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# hash_compare (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que se puede usar con cualquiera de los contenedores asociativos hash \(hash\_map, hash\_multimap, hash\_set o hash\_multiset\) como objeto de parámetro **Traits** predeterminado para ordenar y aplicar algoritmos hash a los elementos que contienen.  
  
## Sintaxis  
  
```  
template<class Key, class Traits = less<Key> >  
   class hash_compare  
   {  
   Traits comp;  
public:  
   const size_t bucket_size = 4;  
   const size_t min_buckets = 8;  
   hash_compare( );  
   hash_compare( Traits pred );  
   size_t operator( )( const Key& _Key ) const;  
   bool operator( )(   
      const Key& _Key1,  
      const Key& _Key2  
   ) const;  
   };  
```  
  
## Comentarios  
 Cada contenedor asociativo de hash almacena un objeto traits hash de tipo **Traits** \(un parámetro de plantilla\).  Puede derivar una clase de una especialización de hash\_compare para reemplazar de forma selectiva ciertas funciones y objetos o puede proporcionar su propia versión de esta clase si cumple ciertos requisitos mínimos.  En concreto, para un objeto hash\_comp de tipo **hash\_compare\<Key, Traits\>**, los contenedores anteriores requieren el siguiente comportamiento:  
  
-   Para todos los valores `_Key` de tipo **Key**, la llamada **hash\_comp**\(`_Key`\) actúa como función hash, que produce una distribución de valores de tipo **size\_t**.  La función suministrada por hash\_compare devuelve `_Key`.  
  
-   Para cualquier valor `_Key1` de tipo **Key** que preceda a `_Key2` en la secuencia y que tenga el mismo valor hash \(valor devuelto por la función hash\), **hash\_comp**\(`_Key2`, `_Key1`\) es false.  La función debe imponer una ordenación total en los valores de tipo **Key**.  La función proporcionada por hash\_compare devuelve *comp*\(`_Key2`, `_Key1`\)`,` donde *comp* es un objeto almacenado de tipo **Traits** que puede especificar al construir el objeto hash\_comp.  Para el tipo de parámetro **Traits** predeterminado **less\<Key\>**, los criterios de ordenación nunca disminuyen en valor.  
  
-   La constante entera **bucket\_size** especifica el número medio de elementos por “depósito” \(entrada de tabla hash\) que el contenedor debe intentar no superar.  Debe ser mayor que cero.  El valor proporcionado por hash\_compare es 4.  
  
-   La constante entera **min\_buckets** especifica el número mínimo de depósitos que se deben mantener en la tabla hash.  Debe ser una potencia de dos y mayor que cero.  El valor proporcionado por hash\_compare es 8.  
  
 En Visual C\+\+ .NET 2003, los miembros de los archivos de encabezado [\<hash\_map\>](../standard-library/hash-map.md) y [\<hash\_set\>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext.  Vea [El espacio de nombres stdext](../standard-library/stdext-namespace.md) para obtener más información.  
  
## Ejemplo  
 Vea los ejemplos de [hash\_map::hash\_map](../Topic/hash_map::hash_map.md), [hash\_multimap::hash\_multimap](../Topic/hash_multimap::hash_multimap.md), [hash\_set::hash\_set](../Topic/hash_set::hash_set.md) y [hash\_multiset::hash\_multiset](../Topic/hash_multiset::hash_multiset.md) para ver ejemplos sobre cómo declarar y usar hash\_compare.  
  
## Requisitos  
 **Encabezado:** \<hash\_map\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)