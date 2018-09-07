---
title: raw_storage_iterator (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
dev_langs:
- C++
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527213eb8e696caa97e307c643929118dd954965
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101020"
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator (Clase)

Una clase de adaptador que se proporciona para permitir que los algoritmos almacenen sus resultados en memoria sin inicializar.

## <a name="syntax"></a>Sintaxis

```cpp
template <class OutputIterator, class Type>
class raw_storage_iterator
```

### <a name="parameters"></a>Parámetros

*OutputIterator*<br/>
Especifica el iterador de salida para el objeto que se almacena.

*Type*<br/>
Tipo de objeto al que se va a asignar almacenamiento.

## <a name="remarks"></a>Comentarios

La clase describe un iterador de salida que construye objetos del tipo `Type` en la secuencia que genera. Un objeto de clase `raw_storage_iterator` \< **ForwardIterator**, **tipo**> accede al almacenamiento a través de un objeto de iterador hacia delante, de clase `ForwardIterator`, especifique cuándo se Construya el objeto. Para un objeto first de la clase `ForwardIterator`, la expresión  **& \*primera** debe designar el almacenamiento no construido para el siguiente objeto (de tipo `Type`) en la secuencia generada.

Esta clase de adaptador se usa cuando es necesario separar la asignación de memoria y la construcción de objetos. `raw_storage_iterator` puede usarse para copiar objetos en el almacenamiento no inicializado, como la memoria asignada mediante la función `malloc`.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Crea un iterador de almacenamiento sin formato con un iterador de salida subyacente especificado.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[element_type](#element_type)|Proporciona un tipo que describe un elemento para almacenar un iterador de almacenamiento sin formato.|
|[iter_type](#iter_type)|Proporciona un tipo que describe un iterador que subyace a un iterador de almacenamiento sin formato.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator*](#op_star)|Un operador de desreferencia usado para implementar la expresión de iterador de salida \* `ii`  =  `x`.|
|[operator=](#op_eq)|Un operador de asignación usado para implementar la expresión de iterador de almacenamiento sin formato \* `i`  =  `x` para almacenar en memoria.|
|[operator++](#op_add_add)|Operadores de preincremento y prostincremento para los iteradores de almacenamiento sin formato.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<memory>

**Espacio de nombres:** std

## <a name="element_type"></a> raw_storage_iterator::element_type

Proporciona un tipo que describe un elemento para almacenar un iterador de almacenamiento sin formato.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo para el parámetro de plantilla de clase raw_storage_iterator `Type`.

## <a name="iter_type"></a> raw_storage_iterator::iter_type

Proporciona un tipo que describe un iterador que subyace a un iterador de almacenamiento sin formato.

```cpp
typedef ForwardIterator iter_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `ForwardIterator`.

## <a name="op_star"></a>  raw_storage_iterator:: operator\*

Un operador de desreferencia usado para implementar la expresión de iterador de almacenamiento sin formato \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

### <a name="return-value"></a>Valor devuelto

Una referencia al iterador de almacenamiento sin formato

### <a name="remarks"></a>Comentarios

Los requisitos para un `ForwardIterator` que están sin formato iterador de almacenamiento debe satisfacer solo requieren que la expresión \* *ii* = *t* sea válida y no indique nada sobre la **operador** o `operator=` por sí solos. Los operadores de miembro en esta implementación devuelve  **\*esto**, de modo que [operador =](#op_eq)(**constType**&) puede realizar el almacenamiento actual en una expresión, como \* *ptr* = `val`.

### <a name="example"></a>Ejemplo

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
\* Output:
Not constructed.
Copying 5
Constructing 5
*\
```

## <a name="op_eq"></a> raw_storage_iterator::operator=

Operador de asignación usado para implementar la expresión del iterador de almacenamiento sin formato \* *i* = *x* para almacenar en memoria.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

### <a name="parameters"></a>Parámetros

*Val*<br/>
El valor del objeto del tipo `Type` va a insertar en la memoria.

### <a name="return-value"></a>Valor devuelto

El operador inserta `val` en la memoria y, después, devuelve una referencia al iterador de almacenamiento sin formato.

### <a name="remarks"></a>Comentarios

Los requisitos para un `ForwardIterator` estado que el iterador de almacenamiento sin formato debe satisfacer solo requieren que la expresión \* *ii* = *t* sea válida y no indique nada sobre el **operador** o `operator=` por sí solos. Estos operadores miembro devuelven **\*this**.

El operador de asignación construye el siguiente objeto en la secuencia de salida con el valor del iterador almacenado en primer lugar, mediante la evaluación de la ubicación de la nueva expresión **new** ( ( `void` \*)&\* **first**) **Type**( `val`).

### <a name="example"></a>Ejemplo

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
\* Output:
Not constructed.
Copying 5
Constructing 5
*\
```

## <a name="op_add_add"></a> raw_storage_iterator::operator++

Operadores de preincremento y prostincremento para los iteradores de almacenamiento sin formato.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

Un iterador de almacenamiento sin formato o una referencia a un iterador de almacenamiento sin formato.

### <a name="remarks"></a>Comentarios

El primer operador, intenta extraer y almacenar un objeto de tipo `CharType` del flujo de entrada asociado. El segundo operador realiza una copia del objeto, lo incrementa y, después, devuelve la copia.

El primer operador preincrement incrementa el objeto de iterador de salida almacenado y, después, devuelve **\*this**.

El segundo operador preincrement realiza una copia de **\*this**, incrementa el objeto de iterador de salida almacenado y, después, devuelve la copia.

El constructor almacena `first` como el objeto de iterador de salida.

### <a name="example"></a>Ejemplo

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
*it = 2 * i;
};

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
\* Output:
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
*\
```

## <a name="raw_storage_iterator"></a> raw_storage_iterator::raw_storage_iterator

Crea un iterador de almacenamiento sin formato con un iterador de salida subyacente especificado.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
El iterador de reenvío que va a subyacer al objeto `raw_storage_iterator` que se está construyendo.

### <a name="example"></a>Ejemplo

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
\* Output:
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
*\
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
