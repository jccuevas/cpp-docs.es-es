---
title: seed_seq (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs:
- C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e466d8a176d5c4c7fd1e2250373b42ee263a6d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="seedseq-class"></a>seed_seq (Clase)

Almacena un vector de valores enteros sin signo que pueden ofrecer una inicialización aleatorizada para un motor con número aleatorio.

## <a name="syntax"></a>Sintaxis

```cpp
class seed_seq
   {
public:
   // types
   typedef unsigned int result_type;

   // constructors
   seed_seq();
   template <class T>
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions
   template <class RandomAccessIterator>
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions
   size_t size() const;
   template <class OutputIterator>
      void param(OutputIterator dest) const;

   // no copy functions
   seed_seq(const seed_seq&) = delete;
   void operator=(const seed_seq&) = delete;
   };
```

## <a name="types"></a>Tipos

`typedef unsigned int result_type;` El tipo de los elementos de la secuencia de inicialización. Un tipo entero de 32 bits sin signo.

## <a name="constructors"></a>Constructores

`seed_seq();` Constructor predeterminado, inicializa tener una secuencia interna vacía.

`template<class T>` `seed_seq(initializer_list<T> initlist);` Utiliza `initlist` para establecer la secuencia interna.
`T` debe ser un tipo entero.

`template<class InputIterator>` `seed_seq(InputIterator begin, InputIterator end);` Inicializa la secuencia interna utilizando todos los elementos en el intervalo de iterador de entrada proporcionado.
`iterator_traits<InputIterator>::value_type` debe ser un tipo entero.

## <a name="members"></a>Miembros

### <a name="generating-functions"></a>Generación de funciones

`template<class RandomAccessIterator> void generate(RandomAccessIterator begin,          RandomAccessIterator end);` Rellena los elementos de la secuencia proporcionada utilizando un algoritmo interno. La secuencia interna con la que `seed_seq` se inicializó afecta a este algoritmo.
No hace nada si `begin == end`.

### <a name="property-functions"></a>Funciones de propiedad

`size_t size() const;` Devuelve el número de elementos de la `seed_seq`.

`template<class OutputIterator> void param(OutputIterator dest) const;` Copia la secuencia interna en el iterador de salida `dest`.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente utiliza tres constructores y genera salida desde las instancias `seed_seq` resultantes al asignarlo a una matriz. Para obtener un ejemplo que use `seed_seq` con un generador de números aleatorios, vea [\<random>](../standard-library/random.md).

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

```Output
seed_seq::size(): 0
seed_seq::param():
Generating a sequence of 5 elements into an array:
505382999
163489202
3932644188
763126080
73937346

seed_seq::size(): 3
seed_seq::param(): 1701 1729 1791
Generating a sequence of 5 elements into an array:
1730669648
1954224479
2809786021
1172893117
2393473414

seed_seq::size(): 7
seed_seq::param(): 65 32 66 32 67 32 68
Generating a sequence of 5 elements into an array:
3139879222
3775111734
1084804564
2485037668
1985355432
```

## <a name="remarks"></a>Comentarios

Las funciones miembro de esta clase no inician excepciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
