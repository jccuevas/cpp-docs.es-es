---
title: "value_compare (Clase) (&lt;map&gt;) | Microsoft Docs"
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
  - "std::value_compare"
  - "std.value_compare"
  - "map/std::value_compare"
  - "value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare (clase)"
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# value_compare (Clase) (&lt;map&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona un objeto de función que puede comparar los elementos de un mapa y compara los valores de sus claves para determinar el orden relativo en el mapa.  
  
## Sintaxis  
  
```  
class value_compare : public binary_function<value_type, value_type, bool>  
{  
public:  
   bool operator()(const value_type& _Left, const value_type& _Right) const;  
   value_compare(key_compare _Pred) : comp(_Pred);  
   protected:  
      key_compare comp;  
};  
```  
  
## Comentarios  
 El criterio de comparación proporcionado por `value_compare` entre **value\_types** de elementos enteros contenido por un mapa es inducido de una comparación entre las claves de los respectivos elementos por la construcción de la clase auxiliar.  El operador de la función miembro utiliza el objeto **comp** de `key_compare` tipo almacenado en el objeto function proporcionado por `value_compare` para comparar los componentes de criterio de ordenación de dos elementos.  
  
 Para los conjuntos y los conjuntos múltiples, que son contenedores simples donde son idénticos los valores de clave en los valores de elemento, `value_compare` es equivalente a `key_compare`; para los mapas y los multimaps no es, como el valor de los elementos de `pair` de tipo no es idéntico al valor de la clave del elemento.  
  
## Ejemplo  
 Vea el ejemplo para [value\_comp](../Topic/map::value_comp.md) para obtener un ejemplo de cómo declarar y utilizar `value_compare`.  
  
## Requisitos  
 **Encabezado:** \<map\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [binary\_function \(Struct\)](../standard-library/binary-function-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)