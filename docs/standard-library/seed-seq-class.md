---
title: "seed_seq (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::seed_seq"
  - "std::tr1::seed_seq"
  - "tr1.seed_seq"
  - "seed_seq"
  - "std.tr1.seed_seq"
  - "random/std::tr1::seed_seq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "seed_seq (clase)"
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# seed_seq (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Almacena un vector de valores enteros sin signo que pueden ofrecer una inicialización aleatorizada para un motor con número aleatorio.  
  
## Sintaxis  
  
```  
class seed_seq  
{  
public:  
    // types  
    typedef unsigned int result_type;  
  
    // constructors  
    seed_seq();  
  
    template<class T>  
    seed_seq(initializer_list<T> initlist);  
  
    template<class InputIterator>  
    seed_seq(InputIterator begin, InputIterator end);  
  
    // generating functions  
    template<class RandomAccessIterator>  
    void generate(RandomAccessIterator begin, RandomAccessIterator end);  
  
    // property functions  
    size_t size() const;  
  
    template<class OutputIterator>  
    void param(OutputIterator dest) const;  
  
    // no copy functions  
    seed_seq(const seed_seq&) = delete;  
    void operator=(const seed_seq&) = delete;  
};  
```  
  
## Tipos  
 `typedef unsigned int result_type;`   
El tipo de los elementos de la secuencia de inicialización. Un tipo entero de 32 bits sin signo.  
  
## Constructores  
 `seed_seq();`   
Constructor predeterminado, inicializa tener una secuencia interna vacía.  
  
 `template<class T>`   
 `seed_seq(initializer_list<T> initlist);`   
Utiliza `initlist` para establecer la secuencia interna.  
`T` debe ser un tipo entero.  
  
 `template<class InputIterator>`   
 `seed_seq(InputIterator begin, InputIterator end);`   
Inicializa la secuencia interna utilizando todos los elementos en el intervalo de iterador de entrada proporcionado.  
`iterator_traits<InputIterator>::value_type` debe ser un tipo entero.  
  
## Miembros  
  
### Generación de funciones  
 `template<class RandomAccessIterator> void generate(RandomAccessIterator begin, RandomAccessIterator end);`   
Rellena los elementos de la secuencia proporcionada utilizando un algoritmo interno. Este algoritmo se ve afectado por la secuencia interna con la que `seed_seq` se inicializó.  
No hace nada si `begin == end`.  
  
### Funciones de propiedad  
 `size_t size() const;`   
Devuelve el número de elementos de la `seed_seq`.  
  
 `template<class OutputIterator> void param(OutputIterator dest) const;`   
Copia la secuencia interna al iterador de salida `dest`.  
  
## Ejemplo  
 El ejemplo de código siguiente utiliza tres constructores y genera salida desde las instancias `seed_seq` resultantes al asignarlo a una matriz. Para obtener un ejemplo que utiliza `seed_seq` con un generador de números aleatorios, consulte [\<random\>](../standard-library/random.md).  
  
```cpp  
#include <iostream>  
#include <random>  
#include <string>  
#include <array>  
  
using namespace std;  
  
void test(const seed_seq& sseq) {  
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;  
  
    cout << "seed_seq::param(): ";  
    ostream_iterator<unsigned int> out(cout, " ");  
    sseq.param(out);  
    cout << endl;  
  
    cout << "Generating a sequence of 5 elements into an array: " << endl;  
    array<unsigned int, 5> seq;  
    sseq.generate(seq.begin(), seq.end());  
    for (unsigned x : seq) { cout << x << endl; }  
}  
  
int main()  
{  
    seed_seq seed1;  
    test(seed1);  
  
    seed_seq seed2 = { 1701, 1729, 1791 };  
    test(seed2);  
  
    string sstr = "A B C D"; // seed string  
    seed_seq seed3(sstr.begin(), sstr.end());  
    test(seed3);  
}  
```  
  
## Salida  
  
```Output  
  
seed_seq::Size(): seed_seq::param() 0: generar una secuencia de 5 elementos en una matriz: 505382999 163489202 3932644188 763126080 73937346 seed_seq::size(): seed_seq::param() 3: 1701 1729 1791 generar una secuencia de 5 elementos en una matriz: 1730669648 1954224479 2809786021 1172893117 2393473414 seed_seq::size(): seed_seq::param() 7: 32 65 32 66 32 67 68 generar una secuencia de 5 elementos en una matriz : 3139879222 3775111734 1084804564 2485037668 1985355432  
```  
  
## Comentarios  
 Las funciones miembro de esta clase no producen excepciones.  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)