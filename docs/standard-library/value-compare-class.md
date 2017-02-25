---
title: "value_compare (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::value_compare"
  - "std.value_compare"
  - "value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare (clase)"
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# value_compare (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona un objeto de función que puede comparar los elementos de un hash\_map comparando los valores de sus claves para determinar el orden relativo en el hash\_map.  
  
## Sintaxis  
  
```  
class value_compare  
    : std::public binary_function<value_type, value_type, bool>   
{  
public:  
    bool operator( )(  
        const value_type& _Left,  
        const value_type& _Right ) const  
        {  
            return ( comp( _Left.first, _Right.first ) );   
        }  
protected:  
    value_compare( const key_compare& c ) : comp (c) { }  
    key_compare comp;  
};  
```  
  
## Comentarios  
 Los criterios de comparación proporcionados por el value\_compare entre **value\_types** de elementos enteros contenidos en un hash\_map son inducidos de una comparación entre las claves de los respectivos elementos por la construcción de la clase auxiliar.  El operador de la función miembro utiliza el objeto **comp** de `key_compare` tipo almacenado en el objeto function proporcionado por el value\_compare para comparar los componentes de criterio de ordenación de dos elementos.  
  
 Para los hash\_sets y los hash\_multisets, que son contenedores simples donde son idénticos los valores de clave en los valores de elemento, el value\_compare es equivalente a `key_compare`; para los hash\_maps y los hash\_multimaps no son, porque el valor de los elementos de `pair` de tipo no es idéntico al valor de la clave del elemento.  
  
 En Visual C\+\+ .NET 2003, los miembros de los archivos de encabezado [\<hash\_map\>](../standard-library/hash-map.md) y [\<hash\_set\>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext.  Vea [El espacio de nombres stdext](../standard-library/stdext-namespace.md) para obtener más información.  
  
## Ejemplo  
 Vea el ejemplo para [hash\_map::value\_comp](../Topic/hash_map::value_comp.md) para obtener un ejemplo de cómo declarar y utilizar el value\_compare.  
  
## Requisitos  
 **Encabezado:** \<hash\_map\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [binary\_function \(Struct\)](../standard-library/binary-function-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)