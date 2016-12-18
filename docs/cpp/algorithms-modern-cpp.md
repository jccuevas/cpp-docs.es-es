---
title: "Algoritmos (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Algoritmos (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para una programación moderna de C\+\+, recomendamos utilizar los algoritmos en la [Biblioteca de plantillas estándar](../standard-library/cpp-standard-library-reference.md) \(STL\).  Aquí se describen algunos ejemplos importantes:  
  
-   `for_each`, que es el algoritmo predeterminado de recorrido. \(También `transform` para semántica fuera de contexto\).  
  
-   `find_if`, que es el algoritmo de búsqueda predeterminado.  
  
-   `sort`, `lower_bound` y los otros algoritmos de ordenación y búsqueda predeterminados.  
  
 Para escribir un comparador, utilice `<` estricto y utilice  *lambdas con nombre* si es posible.  
  
```cpp  
  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
  
```  
  
## Bucles  
 Cuando sea posible, use bucles `for` basados en intervalos o llamadas de algoritmo, o ambos, en lugar de bucles escritos a mano.  `copy`, `transform`, `count_if`, `remove_if` y otros como ellos son mucho mejor que bucles manuscritos porque su intención es obvia y facilitan la escritura de código sin faltas.  Además, muchos algoritmos STL tienen optimizaciones de implementación que los hacen más eficaces.  
  
 En lugar del antiguo C\+\+ así:  
  
```cpp  
  
for( auto i = strings.begin(); i != strings.end(); ++i ) {  
  :::  
  :::  
}  
  
auto i = v.begin();  
  
for( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
  
```  
  
 Utilice C\+\+ moderno de esta forma:  
  
```cpp  
  
for_each( begin(strings), end(strings), [](string& s) {  
  :::  
  :::  
} );  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; }  );  
  
```  
  
### Bucles basados en intervalo  
 El bucle `for` basado en intervalos es una característica del lenguaje C\+\+11, no un algoritmo de STL.  Pero merece que se mencione en esta explicación sobre los bucles.  Los bucles `for` basados en intervalos son una extensión de la palabra clave `for` y proporcionan una forma adecuada y eficaz de escribir bucles que iteran en un intervalo de valores.  Los contenedores STL, cadenas y matrices de STL están listos para usar bucles `for` basados en intervalo.  Para habilitar esta nueva sintaxis de iteración para el tipo definido por el usuario, agregue la siguiente compatibilidad:  
  
-   Un método `begin` que devuelve un iterador al principio de la estructura y un método `end` que devuelve un iterador al final de la estructura.  
  
-   Compatibilidad en el iterador con estos métodos: `operator*`, `operator!=` y `operator++` \(versión prefija\).  
  
 Estos métodos pueden ser miembros o funciones independientes.  
  
## Números aleatorios  
 No es ningún secreto que la antigua función `rand()` de CRT tiene muchos defectos, que se han explicado en profundidad en la comunidad de C\+\+.  En C\+\+ moderno, no tiene que encargarse de esas limitaciones ni tiene que inventar su propio generador de números aleatorios uniformemente distribuido, ya que las herramientas para crearlos rápida y fácilmente están disponibles en STL, como se muestra en [\<random\>](../standard-library/random.md).  
  
## Vea también  
 [Aquí está otra vez C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)