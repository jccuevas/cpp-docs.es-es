---
title: "Matrices (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "cli::array"
  - "details::array"
  - "lang::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array (palabra clave) [C++]"
  - "matrices [C++]"
  - "matrices [C++], multidimensionales"
  - "declarar matrices, acerca de declarar matrices"
  - "matrices multidimensionales"
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Matrices (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`Platform::Array<T>` escribe en [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)], o la palabra clave de `array` en [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)], se declara una matriz de un tipo y un valor inicial especificados.  
  
## Todas las plataformas  
 La matriz se debe declarar con el modificador de identificador\-a\- objeto \(^\) después del corchete angular de cierre \(\>\) en la declaración.  
  
 El número de elementos de la matriz no es parte del tipo.  Una variable de matriz puede hacer referencia a las matrices de tamaños diferentes.  
  
 A diferencia de C\+\+ estándar, la suscripción no es un sinónimo de la aritmética de punteros y no es conmutativa.  
  
 Para obtener más información sobre matrices, vea:  
  
-   [Covarianza de matrices](../misc/array-covariance.md)  
  
-   [Cómo: Usar matrices en C\+\+\/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)  
  
-   [Cómo: Crear matrices multidimensionales](../misc/how-to-create-multidimension-arrays.md)  
  
-   [Cómo: Crear matrices de matrices administradas \(matrices escalonadas\)](../misc/how-to-create-arrays-of-managed-arrays-jagged-arrays.md)  
  
-   [Cómo: Crear definiciones de tipo para las matrices administradas](../misc/how-to-make-typedefs-for-managed-arrays.md)  
  
-   [Cómo: Usar matrices administradas como parámetros de tipo de plantilla](../misc/how-to-use-managed-arrays-as-template-type-parameters.md)  
  
-   [Listas de argumentos de variables \(...\) \(C\+\+\/CLI\)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)  
  
-   [Cómo: Ordenar matrices](../misc/how-to-sort-arrays.md)  
  
-   [Cómo: Ordenar las matrices mediante criterios personalizados](../misc/how-to-sort-arrays-using-custom-criteria.md)  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Las matrices son miembros del espacio de nombres de `Platform` .  Las matrices pueden ser sólo unidimensionales.  
  
 **Sintaxis**  
  
 El primer ejemplo de sintaxis utiliza la palabra clave de agregado de `ref new` para asignar una matriz.  El segundo ejemplo se declara una matriz local.  
  
```  
  
        [qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = ref new [Platform::]Array< initialization-type > [{initialization-list [,...]}]  
  
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier = {initialization-list [,...]}  
  
```  
  
 *qualifiers* \[opcional\]  
 Uno o más de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [estático](../misc/static-cpp.md).  
  
 `array-type`  
 El tipo de la variable de matriz.  Los tipos válidos son clases de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y tipos fundamentales, clases y structs de referencia, clases y structs de valor, y punteros nativos \(`type``*`\).  
  
 `rank` \[opcional\]  
 Número de dimensiones de la matriz.  Debe ser 1.  
  
 `identifier`  
 El nombre de la variable de matriz.  
  
 `initialization-type`  
 El tipo de los valores que se inicializan la matriz.  Normalmente, `array-type` y `initialization-type` son el mismo tipo.  Sin embargo, los tipos pueden ser diferentes si hay una conversión de `initialization-type` a `array-type`\(por ejemplo, si `initialization-type` se deriva de `array-type`.  
  
 `initialization-list` \[opcional\]  
 Una lista de valores delimitada por comas entre llaves que inicializan elementos de la matriz.  Por ejemplo, si `rank-size-list` era `(3)`, que declara una matriz unidimensional de 3 elementos, `initialization list` podría ser `{1,2,3}`.  
  
 **Comentarios**  
  
 Puede detectar en tiempo de compilación si un tipo es una matriz referencia\- contado con `__is_ref_array(``type``)`.  Para obtener más información, vea [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
### Ejemplos  
 El ejemplo siguiente se crea una matriz unidimensional con 100 elementos.  
  
```  
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
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Sintaxis**  
  
 El primer ejemplo de sintaxis utiliza la palabra clave de `gcnew` para asignar una matriz.  El segundo ejemplo se declara una matriz local.  
  
```  
  
        [qualifiers] [cli::]array<[qualifiers] array-type [,rank] >^ identifier = gcnew [cli::]array< initialization-type [,rank] >(rank-size-list[,...]) [{initialization-list [,...]}]  
  
[qualifiers] [cli::]array<[qualifiers] array-type [,rank] >^ identifier = {initialization-list [,...]}  
  
```  
  
 *qualifiers* \[opcional\]  
 Uno o más de estos especificadores de clase de almacenamiento: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [estático](../misc/static-cpp.md).  
  
 `array-type`  
 El tipo de la variable de matriz.  Los tipos válidos son clases de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y tipos fundamentales, clases y structs de referencia, clases y structs value, punteros nativos \(`type``*`\), y tipos nativo POD \(datos antiguos de nivel\).  
  
 `rank` \[opcional\]  
 Número de dimensiones de la matriz.  El valor predeterminado es 1; el valor máximo es 32.  Cada dimensión de la matriz es en sí mismo una matriz.  
  
 `identifier`  
 El nombre de la variable de matriz.  
  
 `initialization-type`  
 El tipo de los valores que se inicializan la matriz.  Normalmente, `array-type` y `initialization-type` son el mismo tipo.  Sin embargo, los tipos pueden ser diferentes si hay una conversión de `initialization-type` a `array-type`\(por ejemplo, si `initialization-type` se deriva de `array-type`.  
  
 `rank-size-list`  
 Una lista delimitada por comas del tamaño de cada dimensión de la matriz.  Como alternativa, si se especifica el parámetro de `initialization-list` , el compilador puede deducir el tamaño de cada dimensión y `rank-size-list` puede omitir.  Para obtener más información, vea [Cómo: Crear matrices multidimensionales](../misc/how-to-create-multidimension-arrays.md).  
  
 `initialization-list` \[opcional\]  
 Una lista de valores delimitada por comas entre llaves que inicializan elementos de la matriz.  O una lista delimitada por comas de elementos anidados de *initialization\-list* inicializar los elementos de una matriz multidimensional.  
  
 Por ejemplo, si `rank-size-list` era `(3)`, que declara una matriz unidimensional de 3 elementos, `initialization list` podría ser `{1,2,3}`.  Si `rank-size-list` era `(3,2,4)`, que declara una matriz tridimensional de 3 elementos en la primera dimensión, 2 elementos en segundo, y 4 elementos en el tercero, `initialization-list` podrían ser `{{1,2,3},{0,0},{-5,10,-21,99}}`.\)  
  
 **Comentarios**  
  
 `array` está en el espacio de nombres [Espacios de nombres de plataforma, predeterminado y CLI](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) .  
  
 Como C\+\+ estándar, los índices de una matriz cero\- se basan, y una matriz subscripted mediante corchetes \(\[\]\).  A diferencia de C\+\+ estándar, los índices de una matriz multidimensional se especifican en una lista de índices para cada dimensión en lugar de un conjunto de operadores entre corchetes \(\[\]\) para cada dimensión.  Por ejemplo, *identifier*\[*index1*, *index2*\] en lugar de *identifier*\[*index1*\] \[ *index2*\].  
  
 Todas las matrices administradas heredan de `System::Array`.  Cualquier método o propiedad de `System::Array` se puede aplicar directamente a la variable de matriz.  
  
 Cuando asigna una matriz cuyo tipo de elemento está puntero\- a una clase administrada, los elementos son 0 inicializado.  
  
 Cuando asigna una matriz cuyo tipo de elemento es un tipo de valor `V`, se aplican al constructor predeterminado para `V` a cada elemento de matriz.  Para obtener más información, vea [.Equivalentes de .NET Framework para tipos nativos de C\+\+](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).  
  
 En tiempo de compilación, puede detectar si un tipo es una matriz de \(CLR\) de Common Language Runtime con `__is_ref_array(``type``)`.  Para obtener más información, vea [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 El ejemplo siguiente se crea una matriz unidimensional con 100 elementos, y una matriz tridimensional con 3 elementos en la primera dimensión, 5 elementos en segundo, y 6 elementos en el tercero.  
  
```  
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
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)