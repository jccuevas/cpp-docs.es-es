---
title: __vectorcall
ms.date: 10/10/2018
f1_keywords:
- __vectorcall_cpp
- __vectorcall
- _vectorcall
helpviewer_keywords:
- __vectorcall keyword
- __vectorcall
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
ms.openlocfilehash: ab542a7fbae286a7f39b66bb4857cd8e8ff6ab59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507229"
---
# <a name="vectorcall"></a>__vectorcall

**Específicos de Microsoft**

El **__vectorcall** convención de llamada especifica que los argumentos para funciones deben pasarse en registros, siempre que sea posible. **__vectorcall** utiliza más registros para argumentos que [__fastcall](../cpp/fastcall.md) o el valor predeterminado [x64 convención de llamada](../build/overview-of-x64-calling-conventions.md) usar. El **__vectorcall** solo se admite la convención de llamada en código nativo en procesadores x86 y x64 que incluyen extensiones SIMD de transmisión por secuencias 2 (SSE2) y versiones posteriores. Use **__vectorcall** acelerar funciones que pasan varios punto flotante o argumentos vectoriales SIMD y realizan operaciones que se benefician de los argumentos cargados en registros. En la lista siguiente se muestra las características que son comunes a las implementaciones x86 y x64 de **__vectorcall**. Las diferencias se explican más adelante en este artículo.

|Elemento|Implementación|
|-------------|--------------------|
|Convención de creación de nombres representativos de C|Sufijo de los nombres de función con dos "arrobas" (\@\@) seguido del número de bytes (en formato decimal) en la lista de parámetros.|
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo la traducción de mayúsculas y minúsculas.|

Mediante el [GV](../build/reference/gd-gr-gv-gz-calling-convention.md) opción del compilador hace que cada función del módulo compile como **__vectorcall** a menos que la función es una función miembro, se declara con un atributo de convención de llamada en conflicto, se utiliza un `vararg` lista de argumentos variable, o tiene el nombre `main`.

Puede pasar tres tipos de argumentos por registro en **__vectorcall** funciones: *tipo entero* valores, *tipo de vector* valores, y *vectorial homogéneo agregado* valores (HVA).

Un tipo entero cumple dos requisitos: se ajusta al tamaño de registro nativo del procesador (por ejemplo, 4 bytes en un equipo x86 u 8 bytes en un equipo x64) y se puede convertir en un entero de longitud de registro y viceversa sin cambiar su representación de bits. Por ejemplo, cualquier tipo que se puede promover a **int** en x86 (**long long** en x64), por ejemplo, un **char** o **corto**, o que se puede convertir en **int** (**long long** en x64) y de nuevo a su tipo original sin cambios es un tipo entero. Tipos enteros son puntero, referencia, y **struct** o **unión** tipos de 4 bytes (8 bytes en x64) o menos. En x64 plataformas, mayor **struct** y **unión** tipos se pasan por referencia a la memoria asignada por el llamador; en x86 plataformas, se pasan por valor en la pila.

Un tipo vectorial es un tipo de punto flotante, por ejemplo, un **float** o **doble**, o un tipo de vector SIMD, por ejemplo, **__m128** o **__m256**.

Un tipo HVA es un tipo compuesto de hasta cuatro miembros de datos que tienen tipos vectoriales idénticos. Un tipo HVA tiene el mismo requisito de alineación que el tipo vectorial de sus miembros. Este es un ejemplo de un HVA **struct** definición que contiene tres tipos de vector idénticos y tiene la alineación de 32 bytes:

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```

Declare las funciones explícitamente con la **__vectorcall** palabra clave en los archivos de encabezado para permitir por separado que compila código vincule sin errores. Las funciones deben ser prototipos para utilizar **__vectorcall**y no se puede usar un `vararg` lista de argumentos de longitud variable.

Una función miembro puede declararse mediante el **__vectorcall** especificador. Ocultar **esto** registro como el primer argumento de tipo entero pasa el puntero.

En las máquinas ARM, **__vectorcall** acepta y omite el compilador.

En el caso de funciones miembro de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los miembros de clase no estáticos, se supone que la convención de llamada especificada durante la declaración está en el punto de la definición. Dada esta definición de clase:

```cpp
struct MyClass {
   void __vectorcall mymethod();
};
```

esto:

```cpp
void MyClass::mymethod() { return; }
```

equivale a esto:

```cpp
void __vectorcall MyClass::mymethod() { return; }
```

El **__vectorcall** se debe especificar el modificador de convención de llamada cuando un puntero a un **__vectorcall** se crea la función. El ejemplo siguiente se crea un **typedef** para un puntero a un **__vectorcall** función que toma cuatro **doble** argumentos y devuelve un **__m256**valor:

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```

Para ofrecer compatibilidad con versiones anteriores, **_vectorcall** es un sinónimo de **__vectorcall** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md)se especifica.

## <a name="vectorcall-convention-on-x64"></a>Convención __vectorcall en x64

El **__vectorcall** convención de llamada en x64 amplía la x64 estándar para aprovechar registros adicionales de la convención de llamada. Los argumentos de tipo entero y los argumentos de tipo vectorial se asignan a registros en función de su posición en la lista de argumentos. Los argumentos de HVA se asignan a los registros vectoriales no usados.

Cuando cualquiera de los cuatro primeros argumentos, por orden, de izquierda a derecha, son argumentos de tipo entero, se pasan en el registro correspondiente a esa posición: RCX, RDX, R8 o R9. Oculto **esto** puntero se trata como el primer argumento de tipo entero. Cuando un argumento de HVA de uno de los cuatro primeros argumentos no se puede pasar en los registros disponibles, se pasa en su lugar una referencia a la memoria asignada por el llamador en el registro correspondiente de tipo entero. Los argumentos de tipo entero después de la cuarta posición de parámetro se pasan en la pila.

Cuando cualquiera de los seis primeros argumentos, por orden, de izquierda a derecha, son argumentos de tipo vectorial, se pasan por valor en los registros vectoriales de SSE 0 a 5, según la posición del argumento. Punto flotante y **__m128** tipos se pasan en registros de XMM, y **__m256** tipos se pasan en registros de YMM registra. Esto difiere de la convención de llamada x64 estándar, porque los tipos de vector se pasan por valor, no por referencia, y se utilizan registros adicionales. El espacio de pila de sombra asignado para argumentos de tipo vectorial se fija en 8 bytes y el [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) opción no es aplicable. Los argumentos de tipo vectorial en las posiciones séptima y posteriores de parámetros se pasan en la pila por referencia a la memoria asignada por el llamador.

Una vez para los argumentos vectoriales, los miembros de datos de los argumentos de HVA se asignan en orden ascendente, a los registros vectoriales sin usar XMM0 a XMM5 (o YMM0 a YMM5, para **__m256** tipos), siempre que haya suficientes registros está disponible para todo el HVA. Si no hay suficientes registros disponibles, el argumento de HVA se pasa por referencia a la memoria asignada por el llamador. El espacio de sombra de pila para un argumento de HVA se fija en 8 bytes con contenido sin definir. Los argumentos de HVA se asignan, por orden, de izquierda a derecha, a los registros de la lista de parámetros, y pueden estar en cualquier posición. Los argumentos de HVA de una de las cuatro primeras posiciones de argumento que no están asignadas a registros vectoriales se pasan por referencia en el registro entero que corresponde a esa posición. Los argumentos de HVA que se pasan por referencia después de la cuarta posición de parámetro se insertan en la pila.

Resultados de **__vectorcall** funciones se devuelven por valor en los registros cuando sea posible. Los resultados de tipo entero, incluidos structs o uniones de 8 bytes o menos, se devuelven por valor en RAX. Los resultados de tipo vectorial se devuelven por valor en XMM0 o YMM0, dependiendo del tamaño. Cada elemento de datos de los resultados de HVA se devuelve por el valor en los registros XMM0:XMM3 o YMM0:YMM3, según el tamaño del elemento. Los tipos de resultado que no se adaptan a los registros correspondientes se devuelven por referencia a la memoria asignada por el llamador.

El llamador en el x64 mantiene la pila de implementación de **__vectorcall**. El código de prólogo y epílogo del llamador asigna y borra la pila de la función llamada. Los argumentos se insertan en la pila de derecha a izquierda y el espacio de pila de sombra se asigna para los argumentos pasados en registros.

Ejemplos:

```cpp
// crt_vc64.c
// Build for amd64 with: cl /arch:AVX /W3 /FAs crt_vc64.c
// This example creates an annotated assembly listing in
// crt_vc64.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in RCX, b in XMM1, c in R8, d in XMM3, e in YMM4,
// f in XMM5, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in RCX, c in R8, d in R9, and e pushed on stack.
// Passes b by element in [XMM0:XMM1];
// b's stack shadow area is 8-bytes of undefined value.
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: Discontiguous HVA
// Passes a in RCX, b in XMM1, d in XMM3, and e is pushed on stack.
// Passes c by element in [YMM0,YMM2,YMM4,YMM5], discontiguous because
// vector arguments b and d were allocated first.
// Shadow area for c is an 8-byte undefined value.
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in RCX, c in R8, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5], each with
// stack shadow areas of an 8-byte undefined value.
// Return value in RAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM0:XMM1], b passed by reference in RDX, c in YMM2,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

## <a name="vectorcall-convention-on-x86"></a>Convención __vectorcall en x86

El **__vectorcall** sigue de convención de llamada la **__fastcall** convención para argumentos de tipo entero de 32 bits y se aprovecha de los registros vectoriales de SSE para argumentos HVA y tipo de vector.

Los dos primeros argumentos de tipo entero que se encuentran en la lista de parámetros de izquierda a derecha se colocan en ECX y EDX, respectivamente. Oculto **esto** puntero se trata como el primer argumento de tipo entero y se pasa en ECX. Los seis primeros argumentos de tipo de vector se pasan por valor en los registros vectoriales de SSE del 0 al 5, en los registros de XMM o YMM, dependiendo del tamaño del argumento.

Los seis primeros argumentos de tipo vectorial, por orden, de izquierda a derecha, se pasan por valor en los registros vectoriales de SSE del 0 al 5. Punto flotante y **__m128** tipos se pasan en registros de XMM, y **__m256** tipos se pasan en registros de YMM registra. No se asigna ningún espacio de pila de sombra para los argumentos de tipo de vector pasados por registro. Los argumentos de tipo de vector séptimo y posteriores se pasan en la pila por referencia a la memoria asignada por el llamador. La limitación de error del compilador [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) no es aplicable a estos argumentos.

Una vez para los argumentos vectoriales, los datos de los miembros de los argumentos de HVA se asignan en orden ascendente a vectoriales sin usar registra XMM0 a XMM5 (o YMM0 a YMM5, para **__m256** tipos), siempre que haya suficientes registros está disponible para todo el HVA. Si no hay suficientes registros disponibles, el argumento de HVA se pasa en la pila por referencia a la memoria asignada por el llamador. No se asigna ningún espacio de sombra de pila para un argumento de HVA. Los argumentos de HVA se asignan, por orden, de izquierda a derecha, a los registros de la lista de parámetros, y pueden estar en cualquier posición.

Resultados de **__vectorcall** funciones se devuelven por valor en los registros cuando sea posible. Los resultados de tipo entero, incluidos structs o uniones de 4 bytes o menos, se devuelven por valor en EAX. Los structs y uniones de tipo entero de 8 bytes o menos se devuelven por valor en EDX:EAX. Los resultados de tipo vectorial se devuelven por valor en XMM0 o YMM0, dependiendo del tamaño. Cada elemento de datos de los resultados de HVA se devuelve por el valor en los registros XMM0:XMM3 o YMM0:YMM3, según el tamaño del elemento. Otros tipos de resultado se devuelven por referencia a la memoria asignada por el llamador.

El x86 implementací **__vectorcall** sigue la convención de argumentos que se insertan en la pila de derecha a izquierda por el llamador y la función llamada borra la pila justo antes de regresar. Solo los argumentos que no se colocan en registros se insertan en la pila.

Ejemplos:

```cpp
// crt_vc86.c
// Build for x86 with: cl /arch:AVX /W3 /FAs crt_vc86.c
// This example creates an annotated assembly listing in
// crt_vc86.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in ECX, b in XMM0, c in EDX, d in XMM1, e in YMM2,
// f in XMM3, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in ECX, c in EDX, d and e pushed on stack.
// Passes b by element in [XMM0:XMM1].
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: HVA assigned after vector types
// Passes a in ECX, b in XMM0, d in XMM1, and e in EDX.
// Passes c by element in [YMM2:YMM5].
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in ECX, c in EDX, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5].
// Return value in EAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM1:XMM2], b passed by reference in ECX, c in YMM0,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

**Fin de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)