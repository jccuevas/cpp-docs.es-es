---
title: Alinear (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- align_cpp
dev_langs:
- C++
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae88262724dfec5702e2769eb10e076502c09342
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418255"
---
# <a name="align-c"></a>align (C++)

En Visual Studio 2015 y versiones posteriores, use el estándar C ++ 11 `alignas` especificador para la alineación del control. Para obtener más información, consulte [alineación](../cpp/alignment-cpp-declarations.md).

**Específicos de Microsoft**

Use `__declspec(align(#))` para controlar con precisión la alineación de datos definidos por el usuario (por ejemplo, asignaciones estáticas o datos automáticos en una función).

## <a name="syntax"></a>Sintaxis

> **__declspec (align (** *#* **))** *declarador*  

## <a name="remarks"></a>Comentarios

Las aplicaciones de escritura que utilizan las últimas instrucciones de procesador presentan nuevas restricciones y problemas. En particular, muchas nuevas instrucciones requieren que los datos se alineen con límites de 16 bytes. Además, la alineación de datos utilizados con frecuencia en el tamaño de la línea de la memoria caché de un procesador concreto mejora el rendimiento de la memoria caché. Por ejemplo, si define una estructura cuyo tamaño es inferior a 32 bytes, puede que desee alinearla en 32 bytes para asegurarse de que los objetos de ese tipo de estructura se almacenen en caché de forma eficaz.

\# es el valor de alineación. Las entradas válidas son potencias enteras de dos desde 1 hasta 8192 (bytes), como 2, 4, 8, 16, 32 o 64. `declarator` corresponde a los datos que se declaran como alineados.

Para obtener información sobre cómo devolver un valor de tipo `size_t` que es el requisito de alineación del tipo, consulte [__alignof](../cpp/alignof-operator.md). Para obtener información acerca de cómo declarar punteros sin alinear cuando se destinan a procesadores de 64 bits, consulte [__unaligned](../cpp/unaligned.md).

Puede utilizar `__declspec(align(#))` al definir `struct`, `union` o `class`, o al declarar una variable.

El compilador no garantiza ni intenta se conserve el atributo de alineación de datos durante una operación de transformación de datos o copia. Por ejemplo, [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) puede copiar una estructura declarada con `__declspec(align(#))` en cualquier ubicación. Tenga en cuenta que normal asignadores: por ejemplo, [malloc](../c-runtime-library/reference/malloc.md), C++ [new (operador)](new-operator-cpp.md)y los asignadores de Win32: devuelven memoria que no normalmente está lo suficientemente alineada para `__declspec(align(#))` estructuras o matrices de estructuras. Para garantizar que el destino de una operación de transformación de datos o copia está correctamente alineado, utilice [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), o escribir su propio asignador.

No puede especificar la alineación de los parámetros de funciones. Cuando los datos que tiene un atributo de alineación se pasan como un valor en la pila, la alineación se controla mediante la convención de llamada. Si la alineación de los datos es importante en la función llamada, copie el parámetro en la memoria alineada correctamente antes de su uso.

Sin `__declspec(align(#))`, el compilador suele alinea los datos en los límites naturales basándose en el procesador de destino y el tamaño de los datos, hasta los límites de 4 bytes en procesadores de 32 bits y los límites de 8 bytes en procesadores de 64 bits. Datos en clases o estructuras está alineados en la clase o estructura como mínimo de su alineación natural y el valor actual de empaquetado (desde #pragma `pack` o **/Zp** opción del compilador).

Este ejemplo muestra el uso de `__declspec(align(#))`:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Ahora, este tipo tiene un atributo de alineación de 32 bytes. Esto significa que todas las instancias estáticas y automáticas empiezan en un límite de 32 bytes. Tipos de estructura adicionales declarados con este tipo como un miembro conservan el atributo de alineación de este tipo, es decir, cualquier estructura con `Str1` como un elemento tiene un atributo de alineación de al menos 32.

Tenga en cuenta que `sizeof(struct Str1)` es igual a 32. Esto implica que si se crea una matriz de objetos Str1, y si la base de la matriz tiene una alineación de 32 bytes, cada miembro de la matriz tiene también una alineación de 32 bytes. Para crear una matriz cuya base esté alineada correctamente en la memoria dinámica, utilice [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), o escribir su propio asignador.

El valor `sizeof` para cualquier estructura es el desplazamiento del miembro final, más el tamaño de ese miembro, redondeado al múltiplo más próximo del mayor valor de alineación de los miembros o del valor total de alineación de estructura, el que sea mayor.

El compilador utiliza estas reglas para la alineación de la estructura:

- A menos que se reemplace con `__declspec(align(#))`, la alineación de un miembro de estructura escalar es el mínimo de su tamaño y empaquetado actual.

- A menos que se reemplace con `__declspec(align(#))`, la alineación de una estructura es el máximo de las alineaciones individuales de sus miembros.

- Un miembro de estructura se coloca en un desplazamiento desde el principio de su estructura principal que es el múltiplo más pequeño de su alineación mayor o igual que el desplazamiento del final del miembro anterior.

- El tamaño de una estructura es el múltiplo más pequeño de su alineación, que es mayor o igual que el desplazamiento del final de su último miembro.

`__declspec(align(#))` solo puede aumentar restricciones de alineación.

Para obtener más información, consulte:

- [Ejemplos para alinear](#vclrfalignexamples)

- [Definir tipos nuevos con __declspec(align(#))](#vclrf_declspecaligntypedef)

- [Alinear los datos en almacenamiento Local de subprocesos](#vclrfthreadlocalstorageallocation)

- [Cómo alinear trabajos con empaquetado de datos](#vclrfhowalignworkswithdatapacking)

- [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md) (x64 específico)

##  <a name="vclrfalignexamples"></a> Ejemplos para alinear

En los ejemplos siguientes se muestra cómo `__declspec(align(#))` afecta al tamaño y la alineación de estructuras de datos. En los ejemplos se suponen las definiciones siguientes:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

En este ejemplo, la `S1` estructura se define mediante el uso de `__declspec(align(32))`. Todos los usos de `S1` para una definición de variable o en otro tipo de declaraciones tienen una alineación de 32 bytes. `sizeof(struct S1)` devuelve 32 y `S1` tiene 16 bytes de relleno a continuación de los 16 bytes necesarios para contener los cuatro enteros. Cada miembro `int` requiere una alineación de 4 bytes, pero la alineación de la propia estructura se declara como 32. Por lo tanto, la alineación global es 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

En este ejemplo, `sizeof(struct S2)` devuelve 16, que es exactamente la suma de los tamaños de miembro, porque es un múltiplo del mayor requisito de alineación (un múltiplo de 8).

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

En el ejemplo siguiente, `sizeof(struct S3)` devuelve 64.

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

En este ejemplo, observe que `a` tiene la alineación de su tipo natural, en este caso, 4 bytes. Sin embargo, `S1` debe tener una alineación de 32 bytes. Veintiocho bytes de relleno siguen a `a`, de modo que `s1` empieza en la posición de desplazamiento 32. `S4` hereda después el requisito de alineación de `S1`, porque es el requisito de alineación mayor de la estructura. `sizeof(struct S4)` devuelve 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Las tres declaraciones de variable siguientes también utilizan `__declspec(align(#))`. En cada caso, la variable debe tener una alineación de 32 bytes. En el caso de la matriz, la dirección base de la matriz, no cada miembro de la matriz, tiene una alineación de 32 bytes. El valor de `sizeof` para cada miembro de la matriz no se ve afectado por el uso de `__declspec(align(#))`.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Para alinear cada miembro de una matriz, se debe utilizar código como el siguiente:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

En este ejemplo, observe que la alineación de la propia estructura y la alineación del primer elemento tienen el mismo efecto:

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` y `S7` tienen características de alineación, asignación y tamaño idénticas.

En este ejemplo, la alineación de las direcciones iniciales de a, b, c y d son 4, 1, 4 y 1, respectivamente.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

La alineación cuando la memoria se asignó en el montón depende de qué función de asignación se invoque.  Por ejemplo, si utiliza `malloc`, el resultado depende del tamaño de operando. Si *arg* > = 8, la memoria devuelta tiene una alineación de 8 bytes. Si *arg* < 8, la alineación de la memoria devuelta es la primera potencia de 2 inferior a *arg*. Por ejemplo, si utiliza malloc(7), la alineación es de 4 bytes.

##  <a name="vclrf_declspecaligntypedef"></a> Definir tipos nuevos con __declspec(align(#))

Puede definir un tipo con una característica de alineación.

Por ejemplo, puede definir un `struct` con una alineación de valor de esta forma:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Ahora, `aType` y `bType` son el mismo tamaño (8 bytes), pero las variables de tipo `bType` tienen una alineación de 32 bytes.

##  <a name="vclrfthreadlocalstorageallocation"></a> Alinear los datos en almacenamiento Local de subprocesos

El almacenamiento local de subprocesos estáticos (TLS) creado con el atributo `__declspec(thread)` y colocado en la sección de TLS en la imagen funciona para la alineación exactamente igual que los datos estáticos normales. Para crear datos TLS, el sistema operativo asigna a la memoria el tamaño de la sección de TLS y respetando el atributo de la alineación de la sección de TLS.

En este ejemplo se muestran diversas maneras de colocar datos alineados en el almacenamiento local para el subproceso.

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

##  <a name="vclrfhowalignworkswithdatapacking"></a> Cómo alinear trabajos con empaquetado de datos

El **/Zp** opción del compilador y el `pack` pragma tiene el efecto de empaquetar datos para los miembros de estructura y unión. Este ejemplo se muestra cómo **/Zp** y `__declspec(align(#))` trabajan juntos:

```c[[]]
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

En la tabla siguiente se muestra el desplazamiento de cada miembro en una variedad de **/Zp** (o #pragma `pack`) valores, que muestra cómo interactúan ambos.

|Variable|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

Para obtener más información, consulte [/Zp (Alineación de miembros de Struct)](../build/reference/zp-struct-member-alignment.md).

El desplazamiento de un objeto se basa en el desplazamiento del objeto anterior y el valor actual de empaquetado, a menos que el objeto tenga un atributo `__declspec(align(#))`, en cuyo caso la alineación se basa en el desplazamiento del objeto anterior y el valor `__declspec(align(#))` para el objeto.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)  
[Información general sobre las convenciones ABI de ARM](../build/overview-of-arm-abi-conventions.md)  
[Información general sobre las convenciones de llamada x64](../build/overview-of-x64-calling-conventions.md)  
