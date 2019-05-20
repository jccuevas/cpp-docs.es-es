---
title: Matrices (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: e4173c16e13c08a54b36e42183e6e18b6ed4fdc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516200"
---
# <a name="arrays-ccli-and-ccx"></a>Matrices (C++/CLI y C++/CX)

El tipo `Platform::Array<T>` en C++/CX, o la palabra clave **array** en C++/CLI, declara una matriz de un tipo y valor inicial especificados.

## <a name="all-platforms"></a>Todas las plataformas

La matriz debe declararse con el modificador de identificador de objeto (^) después del corchete angular de cierre (>) en la declaración.
El número de elementos de la matriz no es parte del tipo. Una matriz puede hacer referencia a matrices de distintos tamaños.

A diferencia de C++ estándar, los subíndices no son sinónimo de aritmética de puntero y no son conmutativos.

Para más información sobre las matrices, consulte:

- [Cómo: Usar matrices en C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Listas de argumentos de variables (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Las matrices son miembros del espacio de nombres `Platform`. Las matrices solo pueden ser unidimensionales.

### <a name="syntax"></a>Sintaxis

En el primer ejemplo de la sintaxis se usa la palabra clave agregada **ref new** para asignar una matriz. En el segundo ejemplo se declara una matriz local.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(Opcional) Uno o varios de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).

*array-type*<br/>
El tipo de la variable de matriz. Los tipos válidos son clases y tipos fundamentales de Windows Runtime, clases de referencia y structs, clases de valor y structs y punteros nativos (`type*`).

*rank*<br/>
(Opcional) El número de dimensiones de la matriz. Debe ser 1.

*identifier*<br/>
El nombre de la variable de matriz.

*initialization-type*<br/>
El tipo de los valores que inicializan la matriz. Por lo general, *array-type* y *initialization-type* son el mismo tipo. Sin embargo, los tipos pueden ser diferentes si hay una conversión de *initialization-type* a *array-type*;por ejemplo, si *initialization-type* se deriva de *array-type*.

*initialization-list*<br/>
(Opcional) Una lista delimitada por comas de valores entre llaves que inicializan los elementos de la matriz. Por ejemplo, si *rank-size-list* fuera `(3)`, que declara una matriz unidimensional de 3 elementos, *initialization list* podría ser `{1,2,3}`.

### <a name="remarks"></a>Comentarios

Puede detectar en tiempo de compilación si un tipo es una matriz con recuento de referencias con `__is_ref_array(type)`. Para más información, consulte [Compatibilidad del compilador con rasgos de tipo](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se crea una matriz unidimensional que tiene 100 elementos.

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Sintaxis

En el primer ejemplo de la sintaxis se usa la palabra clave **gcnew** para asignar una matriz. En el segundo ejemplo se declara una matriz local.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*qualifiers*<br/>
(Opcional) Uno o varios de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).

*array-type*<br/>
El tipo de la variable de matriz. Los tipos válidos son clases y tipos fundamentales de Windows Runtime, clases de referencia y structs, clases de valores y structs, punteros nativos (`type*`) y tipos de POD (Plain Old Data) nativos.

*rank*<br/>
(Opcional) El número de dimensiones de la matriz. El valor predeterminado es 1; el máximo es 32. Cada dimensión de la matriz es en sí misma una matriz.

*identifier*<br/>
El nombre de la variable de matriz.

*initialization-type*<br/>
El tipo de los valores que inicializan la matriz. Por lo general, *array-type* y *initialization-type* son el mismo tipo. Sin embargo, los tipos pueden ser diferentes si hay una conversión de *initialization-type* a *array-type*;por ejemplo, si *initialization-type* se deriva de *array-type*.

*rank-size-list*<br/>
Una lista delimitada por comas del tamaño de cada dimensión de la matriz. Como alternativa, si se especifica el parámetro *initialization-list*, el compilador puede deducir el tamaño de cada dimensión y se puede omitir *rank-size-list*.

*initialization-list*<br/>
(Opcional) Una lista delimitada por comas de valores entre llaves que inicializan los elementos de la matriz. O bien, una lista delimitada por comas de elementos *initialization-list* anidados que inicializan los elementos de en matriz multidimensional.

Por ejemplo, si *rank-size-list* fuera `(3)`, que declara una matriz unidimensional de 3 elementos, *initialization list* podría ser `{1,2,3}`. Si *rank-size-list* fuera `(3,2,4)`, que declara una matriz tridimensional de 3 elementos en la primera dimensión, 2 elementos en la segunda y 4 elementos en la tercera, *initialization-list* podría ser `{{1,2,3},{0,0},{-5,10,-21,99}}`).

### <a name="remarks"></a>Comentarios

**array** se encuentra en el espacio de nombres de [Espacios de nombres de plataforma, predeterminado y CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Como en C++ estándar, los índices de una matriz se basan en cero, y se aplican subíndices a una matriz mediante corchetes ([]). A diferencia de C++ estándar, los índices de una matriz multidimensional se especifican en una lista de índices para cada dimensión, en lugar de en un conjunto de operadores de corchetes ([]) para cada dimensión. Por ejemplo, *identifier*[*index1*, *index2*] en lugar de *identifier*[*index1*][ *index2*].

Todas las matrices administradas heredan de `System::Array`. Cualquier método o propiedad de `System::Array` puede aplicarse directamente a la variable de matriz.

Cuando asigne una matriz cuyo tipo de elemento sea un puntero a una clase administrada, los elementos se inicializan en 0.

Cuando asigne una matriz cuyo tipo de elemento sea un tipo de valor `V`, se aplica el constructor predeterminado de `V` a cada elemento de matriz. Para más información, consulte [Equivalentes de .NET Framework para tipos nativos de C++](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).

En tiempo de compilación, puede detectar si un tipo es una matriz de Common Language Runtime (CLR) con `__is_ref_array(type)`. Para más información, consulte [Compatibilidad del compilador con rasgos de tipo](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se crea una matriz unidimensional que tiene 100 elementos y una matriz tridimensional que tiene 3 elementos en la primera dimensión, 5 elementos en la segunda y 6 elementos en la tercera.

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)