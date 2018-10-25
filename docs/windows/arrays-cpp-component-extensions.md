---
title: Matrices (C++ / c++ / CLI y c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29f84515bfa802af8d6463d34de9b6717c8df044
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061331"
---
# <a name="arrays-ccli-and-ccx"></a>Matrices (C++ / c++ / CLI y c++ / CX)

El `Platform::Array<T>` tipo en C++ / c++ / CX, o la **matriz** palabra clave en C++ / c++ / CLI, declara una matriz de un tipo especificado y el valor inicial.

## <a name="all-platforms"></a>Todas las plataformas

La matriz debe declararse con el modificador de identificador de objeto (^) después del corchete angular de cierre (>) en la declaración.
El número de elementos de la matriz no es parte del tipo. Puede hacer referencia a una variable de matriz para matrices de tamaños diferentes.

A diferencia de C++ estándar, los subíndices no es un sinónimo de aritmética de puntero y no es conmutativo.

Para obtener más información acerca de las matrices, vea:

- [Cómo: Usar matrices en C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Listas de argumentos de variables (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Las matrices son miembros de la `Platform` espacio de nombres. Las matrices solo pueden ser unidimensionales.

### <a name="syntax"></a>Sintaxis

El primer ejemplo de la sintaxis se utiliza el **referencia nuevos** palabra clave agregada para asignar una matriz. El segundo ejemplo declara una matriz local.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*calificadores*<br/>
(Opcional) Uno o varios de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volátil](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [estático](../cpp/static-members-cpp.md).

*tipo de matriz*<br/>
El tipo de la variable de matriz. Tipos válidos son clases de Windows Runtime y tipos fundamentales, las clases ref y structs, las clases de valor y las estructuras y punteros nativos (`type*`).

*rank*<br/>
(Opcional) El número de dimensiones de la matriz. Debe ser 1.

*identifier*<br/>
El nombre de la variable de matriz.

*tipo de inicialización*<br/>
El tipo de los valores que inicializar la matriz. Por lo general, *tipo de matriz* y *tipo de inicialización* son del mismo tipo. Sin embargo, los tipos pueden ser diferentes si hay una conversión de *tipo de inicialización* a *tipo de matriz*— por ejemplo, si *tipo de inicialización* se deriva de *tipo de matriz*.

*lista de inicialización*<br/>
(Opcional) Una lista delimitada por comas de valores entre llaves que inicializar los elementos de la matriz. Por ejemplo, si *rango en la lista de tamaño* eran `(3)`, que declara una matriz unidimensional de 3 elementos *lista de inicialización* podría ser `{1,2,3}`.

### <a name="remarks"></a>Comentarios

Puede detectar en tiempo de compilación si un tipo es una matriz de recuento de referencias con `__is_ref_array(type)`. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

### <a name="examples"></a>Ejemplos

El ejemplo siguiente crea una matriz unidimensional que tiene 100 elementos.

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

El primer ejemplo de la sintaxis se utiliza el **gcnew** palabra clave para asignar una matriz. El segundo ejemplo declara una matriz local.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*calificadores*<br/>
(Opcional) Uno o varios de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volátil](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [estático](../cpp/static-members-cpp.md).

*tipo de matriz*<br/>
El tipo de la variable de matriz. Tipos válidos son clases de Windows Runtime y tipos fundamentales, las clases ref y structs, las clases de valor y structs, punteros nativos (`type*`) y tipos nativos de POD (datos antiguos).

*rank*<br/>
(Opcional) El número de dimensiones de la matriz. El valor predeterminado es 1; el máximo es 32. Cada dimensión de la matriz es una matriz.

*identifier*<br/>
El nombre de la variable de matriz.

*tipo de inicialización*<br/>
El tipo de los valores que inicializar la matriz. Por lo general, *tipo de matriz* y *tipo de inicialización* son del mismo tipo. Sin embargo, los tipos pueden ser diferentes si hay una conversión de *tipo de inicialización* a *tipo de matriz*— por ejemplo, si *tipo de inicialización* se deriva de *tipo de matriz*.

*rango en la lista de tamaño*<br/>
Una lista delimitada por comas del tamaño de cada dimensión de la matriz. Como alternativa, si la *lista de inicialización* parámetro se especifica, el compilador puede deducir el tamaño de cada dimensión y *rango en la lista de tamaño* puede omitirse.

*lista de inicialización*<br/>
(Opcional) Una lista delimitada por comas de valores entre llaves que inicializar los elementos de la matriz. O una lista delimitada por comas de anidado *lista de inicialización* elementos que inicializan los elementos de una matriz multidimensional.

Por ejemplo, si *rango en la lista de tamaño* eran `(3)`, que declara una matriz unidimensional de 3 elementos *lista de inicialización* podría ser `{1,2,3}`. Si *rango en la lista de tamaño* eran `(3,2,4)`, que declara una matriz tridimensional de 3 elementos de la primera dimensión, 2 elementos en el segundo y 4 elementos en la tercera, *lista de inicialización* podría ser `{{1,2,3},{0,0},{-5,10,-21,99}}`.)

### <a name="remarks"></a>Comentarios

**matriz** está en el [de plataforma, predeterminado y cli de espacios de nombres](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) espacio de nombres.

Como C++ estándar, los índices de matriz son de base cero y una matriz es de subíndice utilizando corchetes ([]). A diferencia de C++ estándar, los índices de una matriz multidimensional se especifican en una lista de los índices de cada dimensión en lugar de un conjunto de operadores de corchetes ([]) para cada dimensión. Por ejemplo, *identificador*[*index1*, *index2*] en lugar de *identificador*[*index1*] [ *index2*].

Todas las matrices administradas se heredan de `System::Array`. Cualquier método o propiedad de `System::Array` pueden aplicarse directamente a la variable de matriz.

Cuando asigne una matriz cuyo tipo de elemento es el puntero-para una clase administrada, los elementos son inicializado de 0.

Cuando asigne una matriz cuyo tipo de elemento es un tipo de valor `V`, el constructor predeterminado para `V` se aplica a cada elemento de matriz. Para obtener más información, consulte [equivalentes de .NET Framework para tipos nativos de C++ (C++ / c++ / CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).

En tiempo de compilación, puede detectar si un tipo es una matriz de runtime (CLR) de lenguaje común con `__is_ref_array(type)`. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se crea una matriz unidimensional que tiene 100 elementos y una matriz tridimensional que tiene 6 elementos en la tercera, 5 elementos en la segunda y 3 elementos en la primera dimensión.

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

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)