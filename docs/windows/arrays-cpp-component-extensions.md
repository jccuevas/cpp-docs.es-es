---
title: Matrices (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cli::array
- details::array
- lang::array
dev_langs: C++
helpviewer_keywords:
- array keyword [C++]
- declaring arrays, about declaring arrays
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 343f2369260531e828ea8db27cee5e52ea18fd31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="arrays-c-component-extensions"></a>Matrices (Extensiones de componentes de C++)
El `Platform::Array<T>` tipo en C++ / CX, o `array` palabra clave en C++ / CLI, declara una matriz de un tipo especificado y el valor inicial.  
  
## <a name="all-platforms"></a>Todas las plataformas  
 La matriz debe declararse con el modificador "identificador a objeto" (^) después del corchete angular de cierre (>) en la declaración.  
 El número de elementos de la matriz no forma parte del tipo. Una variable de matriz puede hacer referencia a las matrices de tamaños diferentes.  
  
 A diferencia de C++ estándar, subíndices no es un sinónimo de la aritmética de puntero y no es conmutativa.  
  
 Para obtener más información acerca de las matrices, vea:  
  
-   [Cómo: Usar matrices en C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
    
-   [Listas de argumentos de variables (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 Las matrices son miembros de la `Platform` espacio de nombres. Matrices sólo pueden ser unidimensionales.  
  
### <a name="syntax"></a>Sintaxis  
  
 El primer ejemplo de la sintaxis se utiliza el `ref new` palabra clave agregada para asignar una matriz. El segundo ejemplo declara una matriz local.  
  
```  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *calificadores* [opcional]  
 Uno o varios de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volátiles](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [estático](../cpp/static-members-cpp.md).  
  
 `array-type`  
 El tipo de la variable de matriz. Los tipos válidos son clases en tiempo de ejecución de Windows y los tipos fundamentales, clases ref y structs, las clases de valor y estructuras y punteros nativos (`type*`).  
  
 `rank`[opcional]  
 El número de dimensiones de la matriz. Debe ser 1.  
  
 `identifier`  
 El nombre de la variable de matriz.  
  
 `initialization-type`  
 El tipo de los valores que se inicialice la matriz. Por lo general, `array-type` y `initialization-type` son del mismo tipo. Sin embargo, los tipos pueden ser diferentes si hay una conversión de `initialization-type` a `array-type`: por ejemplo, si `initialization-type` se deriva de `array-type`.  
  
 `initialization-list`[opcional]  
 Una lista delimitada por comas de valores de llaves que inicializan los elementos de la matriz. Por ejemplo, si `rank-size-list` estaban `(3)`, que declara una matriz unidimensional de 3 elementos `initialization list` podría ser `{1,2,3}`.  
  
### <a name="remarks"></a>Comentarios  
  
 Puede detectar en tiempo de compilación si un tipo es una matriz de recuento de referencias con `__is_ref_array(type)`. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
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
  
 El primer ejemplo de la sintaxis se utiliza el `gcnew` palabra clave que se va a asignar una matriz. El segundo ejemplo declara una matriz local.  
  
```  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier = 
    {initialization-list [,...]}  
```  
  
 *calificadores* [opcional]  
 Uno o varios de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volátiles](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [estático](../cpp/static-members-cpp.md).  
  
 `array-type`  
 El tipo de la variable de matriz. Los tipos válidos son clases en tiempo de ejecución de Windows y los tipos fundamentales, clases ref y structs, las clases de valor y estructuras, punteros nativos (`type*`) y los tipos nativos de POD (datos antiguos sin formato).  
  
 `rank`[opcional]  
 El número de dimensiones de la matriz. El valor predeterminado es 1; el valor máximo es 32. Cada dimensión de la matriz es una matriz.  
  
 `identifier`  
 El nombre de la variable de matriz.  
  
 `initialization-type`  
 El tipo de los valores que se inicialice la matriz. Por lo general, `array-type` y `initialization-type` son del mismo tipo. Sin embargo, los tipos pueden ser diferentes si hay una conversión de `initialization-type` a `array-type`: por ejemplo, si `initialization-type` se deriva de `array-type`.  
  
 `rank-size-list`  
 Una lista delimitada por comas de tamaño de cada dimensión de la matriz. Como alternativa, si la `initialization-list` se especifica el parámetro, el compilador puede deducir el tamaño de cada dimensión y `rank-size-list` puede omitirse. 
  
 `initialization-list`[opcional]  
 Una lista delimitada por comas de valores de llaves que inicializan los elementos de la matriz. O una lista delimitada por comas de anidado *lista de inicialización* elementos que inicializan los elementos de una matriz multidimensional.  
  
 Por ejemplo, si `rank-size-list` estaban `(3)`, que declara una matriz unidimensional de 3 elementos `initialization list` podría ser `{1,2,3}`. IF `rank-size-list` estaban `(3,2,4)`, que declara una matriz tridimensional de 3 elementos en la primera dimensión, 2 elementos en el segundo y 4 elementos en la tercera, `initialization-list` podría ser `{{1,2,3},{0,0},{-5,10,-21,99}}`.)  
  
### <a name="remarks"></a>Comentarios  
  
 `array`en el [plataforma, predeterminado y cli espacios de nombres](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) espacio de nombres.  
  
 Como C++ estándar, los índices de una matriz son de base cero y una matriz está indicada mediante el uso de corchetes ([]). A diferencia de C++ estándar, los índices de una matriz multidimensional se especifican en una lista de los índices de cada dimensión en lugar de un conjunto de operadores de corchetes ([]) para cada dimensión. Por ejemplo, *identificador*[*index1*, *index2*] en lugar de *identificador*[*index1*] [ *index2*].  
  
 Todas las matrices administradas se heredan de `System::Array`. Cualquier método o propiedad de `System::Array` pueden aplicarse directamente a la variable de matriz.  
  
 Cuando asigne una matriz cuyo tipo de elemento es el puntero-a una clase administrada, los elementos son inicializa a 0.  
  
 Cuando asigne una matriz cuyo tipo de elemento es un tipo de valor `V`, el constructor predeterminado para `V` se aplica a cada elemento de matriz. Para obtener más información, consulte [equivalentes de .NET Framework para tipos nativos de C++ (C++ / CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).  
  
 En tiempo de compilación, puede detectar si un tipo es una matriz de runtime (CLR) de lenguaje común con `__is_ref_array(type)`. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea una matriz unidimensional que tiene 100 elementos y una matriz tridimensional que tiene 3 elementos en la primera dimensión, 5 elementos en el segundo y 6 elementos en el tercer argumento.  
  
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
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)