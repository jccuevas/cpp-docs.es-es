---
title: Optimización de punto de flotante de Microsoft Visual C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35c9263fa6252469124eefb0dfd575ef5bd2ac34
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422742"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Optimización de punto flotante de Microsoft Visual C++

Obtenga un identificador para optimizar el código de punto flotante mediante el método del compilador de Microsoft C++ para administrar la semántica de punto flotante. Crear programas rápidos asegurándose de que solo seguros optimizaciones se realizan en código de punto flotante.

## <a name="optimization-of-floating-point-code-in-c"></a>Optimización del código de punto flotante en C++

Un compilador de optimización de C++ no solo convierte código fuente en código máquina, los organiza las instrucciones máquina de manera que mejorar la eficacia y reducir el tamaño. Por desgracia, muchas optimizaciones comunes no son necesariamente seguros cuando se aplica a operaciones de punto flotante. Un buen ejemplo de esto se puede ver con el siguiente algoritmo de suma, tomado de David Goldberg, "Lo que cada equipo científico debe saber acerca de la aritmética de punto flotante", *informática encuestas*, marzo de 1991, pg. 203:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Esta función agrega n **float** valores del vector de matriz `A`. En el cuerpo del bucle, el algoritmo calcula un valor de "corrección" que, a continuación, se aplica al paso siguiente de la suma. Este método reduce enormemente los errores de redondeo acumulativos en comparación con una simple suma, conservando la complejidad del tiempo o (n).

Un compilador de C++ naïve puede suponer que aritmética de coma flotante sigue las mismas reglas algebraicas como número Real aritmética. Un compilador de este tipo podría, a continuación, erróneamente concluir

> C = T - sum - Y == > (suma + Y) - sum - Y == > 0;

Es decir, que el valor percibido de C siempre es un constante cero. Si este valor constante, a continuación, se propaga a las expresiones subsiguientes, el cuerpo del bucle se reduce a una suma simple. Para ser precisos,

> Y = [i] - C == > Y = [i]<br/>T = suma + Y == > T = suma + [i]<br/>suma = T == > suma = sum + [i]

Por lo tanto, para el compilador naïve, una transformación lógica de la `KahanSum` función sería:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Aunque el algoritmo transformado es más rápido, *no es una representación exacta de la intención del programador*. Se ha quitado completamente la corrección de errores cuidadosamente diseñadas y lo que nos queda con un algoritmo de suma sencilla y directa con todos su error asociado.

Por supuesto un compilador de C++ sofisticado sabría que algebraicas reglas de Real aritmética no generalmente se aplican a aritmética de coma flotante. Sin embargo, incluso un compilador de C++ sofisticado todavía incorrectamente podría interpretar intención del programador.

Tenga en cuenta una optimización comunes que se intenta almacenar varios valores en los registros como sea posible (llamado "registrar" un valor). En el `KahanSum` ejemplo, esta optimización puede intentar registre las variables `C`, `Y` y `T` desde que se utilizan solo dentro del cuerpo del bucle. Si la precisión de registro es 52bits (double) en lugar de 23bits (único), esta optimización eficazmente tipo promociona `C`, `Y` y `T` al tipo **doble**. Si la variable de suma no es del mismo modo registren, permanecerá codificado en precisión simple. Esto transforma la semántica de `KahanSum` al siguiente

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

Aunque `Y`, `T` y `C` ahora se calculan con una mayor precisión, esta nueva codificación puede producir un resultado menos preciso según los valores de `A[]`. Por lo tanto incluso aparentemente inofensivos optimizaciones pueden tener consecuencias negativas.

Estos tipos de problemas de optimización no se restringe al código de punto flotante "difícil". Algoritmos de punto flotante incluso simples pueden producir un error al optimizar de forma incorrecta. Considere la posibilidad de un algoritmo sencillo y directo suma:

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Dado que algunas unidades de punto flotante son capaces de realizar varias operaciones simultáneamente, un compilador puede captar una optimización de reducción escalar. Esta optimización transforma eficazmente la función Sum simple anteriores en lo siguiente:

```cpp
float Sum( const float A[], int n )
{
   int n4 = n-n%4; // or n4=n4&(~3)
   int i;
   float sum=0, sum1=0, sum2=0, sum3=0;
   for (i=0; i<n4; i+=4)
   {
      sum = sum + A[i];
      sum1 = sum1 + A[i+1];
      sum2 = sum2 + A[i+2];
      sum3 = sum3 + A[i+3];
   }
   sum = sum + sum1 + sum2 + sum3;
   for (; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

La función mantiene ahora cuatro sumas independientes, que se pueden procesar simultáneamente en cada paso. Aunque la función optimizada ahora es mucho más rápida, los resultados optimizados pueden ser bastante diferentes de los resultados no optimizada. Para realizar este cambio, el compilador supone asociativa adición de punto flotante; es decir, que estos dos expresiones son equivalentes: `(a + b) + c == a + (b + c)`. Sin embargo, asociatividad no siempre es cierta para números de punto flotante. En lugar de calcular la suma, como:

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

la función transformada ahora calcula el resultado como

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

Para algunos valores de `A[]`, este distintas ordenaciones de las operaciones de adición pueden producir resultados inesperados. Para complicar aún más, algunos programadores puede prever estas optimizaciones y compensar adecuadamente para ellos. En este caso, un programa puede construir la matriz `A` en un orden diferente para que la suma optimizada produce los resultados esperados. Además, en muchos casos la precisión del resultado optimizado puede ser "lo suficientemente". Esto es especialmente cierto cuando la optimización ofrece ventajas de velocidad atractivos. Usuarios de videojuegos, por ejemplo, requieren que mucho la velocidad como sea posible, pero a menudo no requieren cálculos de punto flotante de alta precisión. Creadores de compilador, por tanto, deben proporcionar un mecanismo para que los programadores controlar los objetivos a menudo dispares de velocidad y precisión.

Algunos compiladores de resolver el equilibrio entre la velocidad y precisión proporcionando un conmutador independiente para cada tipo de optimización. Esto permite a los desarrolladores deben deshabilitar las optimizaciones que provocan cambios con precisión de punto flotante para su aplicación en particular. Si bien esta solución puede ofrecer un alto grado de control sobre el compilador, presenta varios problemas adicionales:

- A menudo resulta evidente que se activa para habilitar o deshabilitar.
- Deshabilitar cualquier optimización único negativamente puede afectar al rendimiento del código de punto no flotante.
- Cada conmutador adicional incurre en muchas combinaciones de conmutador nuevo; el número de combinaciones rápidamente es difícil de manejar.

Por lo que aunque proporciona conmutadores independientes para cada optimización puede parecer atractivo, usan compiladores de este tipo puede ser complejo y poco confiables.

Muchos de los compiladores de C++ ofrecen una *coherencia* modelo de punto flotante, (a través de un **/Op** o **/fltconsistency** cambiar) que permite que un desarrollador crear programas compatibles con la semántica estricta de punto flotante. Cuando se activa, este modelo impide que el compilador use mayoría de las optimizaciones en operaciones de punto flotante permitiendo que las optimizaciones de código de punto no flotante. El modelo de coherencia, sin embargo, tiene un lado oscuro. Para devolver resultados de predicción en distintas arquitecturas FPU, casi todas las implementaciones de **/Op** expresiones intermedias redondear al usuario precisión especificada; por ejemplo, considere la siguiente expresión:

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

Para generar resultados coherentes y repetibles en **/Op**, esta expresión se evalúa como si se implementa como se indica a continuación:

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

El resultado final ahora sufre errores de redondeo de precisión sencilla *en cada paso en la evaluación de la expresión*. Aunque esta interpretación estrictamente no infringen las reglas de la semántica de C++, casi nunca es la mejor forma de evaluar las expresiones de punto flotante. Es generalmente más atractivo para calcular intermedias provoca tan alto como precisión tal y como resulta muy práctico. Por ejemplo, sería mejor calcular la expresión `a = b * c + d * e` en una precisión mayor que en

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

o todavía mejor

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

Al calcular los resultados intermedios en una precisión mayor, el resultado final es significativamente más preciso. Irónicamente, mediante el uso de un modelo de coherencia, se aumenta la probabilidad de error con precisión cuando el usuario intenta reducir error deshabilitando las optimizaciones no seguras. Por lo tanto el modelo de coherencia puede reducir drásticamente la eficiencia al tiempo que ofrece ninguna garantía de una mayor precisión. Para los programadores numéricos graves, esto no parece como un equilibrio muy bueno y es el motivo principal que el modelo no generalmente también recibe.

A partir de la versión 8.0 (Visual C++® 2005), Microsoft C++ compilador proporciona una mejor alternativa. Permite a los programadores seleccionar uno de los tres modos de punto flotante generales: fp: precisa, fp: Fast y fp: strict.

- Bajo fp: precisa, solo seguras optimizaciones se realizan en código de punto flotante y, a diferencia de **/Op**, constantemente se realizan los cálculos intermedios en la mayor precisión resulta muy práctica.
- modo fp: Fast relaja las reglas de punto flotante que permite que más agresiva optimización a costa de precisión.
- fp: strict modo proporciona todas la corrección general de fp: precisa al habilitar la semántica de excepciones fp e impide las transformaciones no válidas en la presencia de cambios en el entorno FPU (por ejemplo, cambios en la precisión de registro, redondeo dirección etcetera).

La semántica de excepciones de punto flotante puede controlarse de forma independiente por parte de un conmutador de línea de comandos o una directiva pragma de compilador; de forma predeterminada, se deshabilita la semántica de excepciones de punto flotante en fp: precisa y están habilitados en fp: strict. El compilador también proporciona control sobre la importancia del entorno de FPU y ciertas optimizaciones específicas punto flotante, como las contracciones. Este modelo directa ofrece a los desarrolladores un gran control sobre la compilación del código de punto flotante sin la carga de demasiados modificadores del compilador o la perspectiva de los efectos secundarios no deseados.

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp: modo preciso para la semántica de punto flotante

El modo predeterminado de la semántica de punto flotante es fp: precisa. Cuando se selecciona este modo, el compilador estrictamente se ajusta a un conjunto de reglas de seguridad al optimizar las operaciones de punto flotante. Estas reglas permiten al compilador que genere código máquina eficaz al tiempo que mantiene la precisión de los cálculos de punto flotante. Para facilitar la producción de fast fp programas: modelo preciso deshabilita la semántica de excepciones de punto flotante (aunque pueden habilitarse explícitamente). Microsoft ha seleccionado fp: precisa como el modo de punto flotante de forma predeterminada porque crea programas rápidos y precisos.

Para solicitar explícitamente la fp: modo preciso mediante el compilador de línea de comandos, use el [/fp: precisa](fp-specify-floating-point-behavior.md) cambiar:

> / FP cl: source.cpp precisa

Esto indica al compilador que utilice fp: semántica precisa al generar código para el archivo source.cpp. Fp: modelo preciso también se puede invocar en una función por función utilizando la [float_control compilador pragma](#the-float-control-pragma).

En el fp: modo preciso, el compilador nunca realiza las optimizaciones que perturb la precisión de los cálculos de punto flotante. El compilador siempre se redondeará correctamente en las asignaciones, conversiones de tipo y llamadas a funciones y redondeo intermedio constantemente realizará en la misma precisión tal y como se registra la FPU. Las optimizaciones seguras, como las contracciones, están habilitadas de forma predeterminada. La semántica de excepciones y sensibilidad de entorno FPU están deshabilitados de forma predeterminada.

|fp: semántica precisa|Explicación|
|-|-|
|Semántica de redondeo|Redondeo explícita en las asignaciones, conversiones de tipo y función llama. Expresiones intermedias se evaluará en el registro de precisión.|
|Transformaciones algebraicas|Estricta observancia de álgebra de punto flotante no asociativa, no distributivas, a menos que una transformación se garantiza que siempre generan los mismos resultados.|
|Contracciones|Permite de forma predeterminada. Para obtener más información, vea la sección [la pragma fp_contract](#the-fp-contract-pragma).|
|Orden de evaluación de punto flotante|El compilador puede reordenar la evaluación de expresiones de punto flotante, siempre que no se modifican los resultados finales.|
|Acceso de entorno FPU|Deshabilitada de forma predeterminada. Para obtener más información, vea la sección [el pragma fenv_access](#the-fenv-access-pragma). Se supone que la precisión predeterminada y el modo de redondeo.|
|Semántica de excepciones de punto flotante|Deshabilitada de forma predeterminada. Para obtener más información, consulte [/fp: excepto](fp-specify-floating-point-behavior.md).|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>Redondeo semántica para las expresiones de punto flotante en fp: precisa

Fp: modelo preciso siempre realiza los cálculos intermedios en la precisión práctico más alto, redondeo explícitamente solo en determinados puntos en la evaluación de expresión. Redondeo a la precisión especificada por el usuario siempre se produce en cuatro lugares: (a) cuando se realiza una asignación, (b) cuando se realiza una conversión de tipo, (c) cuando un valor de punto flotante se pasa como argumento a una función y (d) cuando se devuelve un valor de punto flotante de una función. Dado que los cálculos intermedios siempre se realizan en la precisión de registro, la precisión de los resultados intermedios es dependiente de la plataforma (aunque siempre será al menos tan precisa como el usuario especificado precisión precisión).

Considere la posibilidad de la expresión de asignación en el código siguiente. La expresión en el lado derecho de la asignación operador '=' se calcula en precisión de registro y, a continuación, se redondea explícitamente al tipo del lado izquierdo de la asignación.

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

se calcula como

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Para redondear explícitamente un resultado intermedio, presentan una conversión de tipo. Por ejemplo, si se modifica el código anterior agregando explícito convertir el tipo, la expresión intermedia (c * d.) se redondeará al tipo de la conversión de tipo.

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

se calcula como

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Una implicación de este método de redondeo es que algunas transformaciones aparentemente equivalentes realmente no tienen una semántica idéntica. Por ejemplo, la transformación siguiente divide una expresión de asignación único en dos expresiones de asignación.

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

NO es equivalente a

```cpp
float a, b, c, d;
// . . .
a = c+d;
a = b*a;
```

Del mismo modo:

```cpp
a = b*(c+d);
```

NO es equivalente a

```cpp
a = b*(a=c+d);
```

Estas codificaciones no tienen una semántica equivalente porque las codificaciones segundo han introducido una operación de asignación adicionales y, por tanto, un redondeo adicionales punto.

Cuando una función devuelve un valor de punto flotante, se redondeará el valor al tipo de la función. Cuando un valor de punto flotante se pasa como un parámetro a una función, se redondeará el valor al tipo del parámetro. Por ejemplo:

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

se calcula como

```cpp
float sumsqr(float a, float b)
{
    register tmp3 = a*a;
    register tmp4 = b*b;
    register tmp5 = tmp3+tmp4;
    return (float) tmp5;
}
```

Del mismo modo:

```cpp
float w, x, y, z;
double c;
...
c = symsqr(w*x+y, z);
```

se calcula como

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>Redondeo específicas de la arquitectura en fp: precisa

|Procesador|Redondeo de precisión para las expresiones intermedias|
|-|-|
|x86|Expresiones intermedias se calculan en la precisión de 53 bits predeterminado con un intervalo extendido proporcionado por un exponente de 16 bits. Cuando estos valores 53:16 se "vuelcan" en la memoria (como puede ocurrir durante una llamada de función), se va a restringir el intervalo de exponente extendido en 11 bits. Es decir, volcados valores se convierten al formato estándar de precisión doble con solo un exponente de 11 bits.<br/>Un usuario puede cambiar a la precisión extendida de 64 bits de redondeo intermedio modificando la palabra de control de punto flotante mediante `_controlfp` y al habilitar el acceso de entorno FPU (vea [el pragma fenv_access](#the-fenv-access-pragma)). Sin embargo, cuando los valores de registro de la precisión extendida se vuelcan en la memoria, los resultados intermedios todavía se redondeará a precisión doble.<br/>Esta semántica particular está sujeta a cambios.|
|amd64|Semántica de FP en amd64 es ligeramente distinta de otras plataformas. Por motivos de rendimiento, operaciones intermedias se calculan en la precisión más amplia de alguno de los operandos en lugar de en la precisión más amplia disponible.  Para forzar que los cálculos que debe calcularse mediante una mayor precisión que los operandos, los usuarios deben introducir una operación de conversión en al menos un operando en una subexpresión.<br/>Esta semántica particular está sujeta a cambios.|

### <a name="algebraic-transformations-under-fpprecise"></a>Transformaciones algebraicas bajo fp: precisa

Cuando el fp: modo preciso está habilitado, el compilador nunca llevará a cabo transformaciones algebraicas *a menos que el resultado final es idéntico demostrado*. Muchas de las reglas algebraicas familiarizadas para número Real aritméticos no mantenga siempre aritmética de coma flotante. Por ejemplo, las expresiones siguientes son equivalentes para Reals, pero no necesariamente para valores de coma flotante.

|Form|Descripción|
|-|-|
|`(a+b)+c = a+(b+c)`|Regla asociativa para adición|
|`(a*b)*c = a*(b*c)`|Regla asociativa de multiplicación|
|`a*(b+c) = a*b + b*c`|Distribución de multiplicación sobre la suma|
|`(a+b)(a-b) = a*a-b*b`|Factorización algebraico|
|`a/b = a*(1/b)`|División por inverso multiplicativo|
|`a*1.0 = a`|Identidad de multiplicación|

Como se muestra en el ejemplo de introducción a la función `KahanSum`, el compilador podría querer realizar diversas transformaciones algebraicas con el fin de generar programas notablemente más rápidos. Aunque las optimizaciones depende de esas transformaciones algebraicas casi siempre son incorrectas, hay ocasiones para que sean seguros perfectamente. Por ejemplo, en ocasiones es deseable para reemplazar la división por un *constante* valor con la multiplicación por la multiplicación inversa de la constante:

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

Se pueden transformar en

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

Esto es una transformación segura porque el optimizador puede determinar en tiempo de compilación que x / 4.0 == x*(1/4.0) para todos los valores de punto flotante de x, incluidos los valores infinitos y NaN. Si se reemplaza una operación de división con una multiplicación, el compilador puede guardar varios ciclos, especialmente en FPUs que directamente no implementan la división, pero requieren el compilador para generar una combinación de aproximación recíproco y agregar multiplicar instrucciones. El compilador puede realizar una optimización en fp: precisa solo cuando la multiplicación de reemplazo produce exactamente el mismo resultado como la división. El compilador también puede realizar transformaciones triviales bajo fp: precisa, siempre que los resultados son idénticos. Se incluyen los siguientes:

|Form|Descripción
|-|-|
|`(a+b) == (b+a)`|Regla conmutativa para adición|
|`(a*b) == (b*a)`|Regla conmutativa para la multiplicación|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|Multiplicación por 1,0|
|`x/1.0*y == x*y/1.0 == x*y`|División por 1,0|
|`2.0*x == x+x`|Multiplicación por 2.0|

### <a name="contractions-under-fpprecise"></a>Contracciones bajo fp: precisa

Una característica clave de arquitectura de muchas unidades de punto flotante modernas es la capacidad para realizar una multiplicación seguida por una adición como una operación única con ningún error de redondeo intermedio. Por ejemplo, arquitectura Itanium de Intel proporciona instrucciones para cada una de estas operaciones ternarias, combinar (un*b + c), (una*b-c) y (c-a * b), en una sola instrucción de punto flotante (fma, fms y fnma respectivamente). Estas instrucciones solo son más rápidas que la ejecución independiente multiplicar y agregar instrucciones y son más precisas porque no hay ningún redondeo intermedio del producto. Esta optimización significativamente puede acelerar las funciones que contienen varios intercalar multiplicar y agregar las operaciones. Por ejemplo, considere el siguiente algoritmo que calcula el producto escalar de dos vectores de n dimensiones.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Este cálculo puede realizarse una serie de multiplicar-agregar instrucciones de la forma p = p + x [i] * y [i].

La optimización de contracción puede controlarse de forma independiente mediante la `fp_contract` pragma de compilador. De forma predeterminada, el fp: modelo preciso permite contracciones puesto que mejoran la precisión y la velocidad. Bajo fp: precisa, el compilador no se nunca de contrato de una expresión con redondeo explícita.
Ejemplos

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add
etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Orden de evaluación de expresión de punto flotante en fp: precisa

Las optimizaciones que conserva el orden de evaluación de expresiones de punto flotante siempre son seguras y, por tanto, se permiten en fp: modo preciso. Considere la siguiente función que calcula el producto escalar de dos vectores de n dimensiones de precisión simple. El primer bloque de código siguiente es la función original que puede estar codificado por un programador, seguida de la misma función después de una optimización de interpretar bucle parcial.

```cpp
//original function
float dotProduct( float x[], float y[], int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}

//after a partial loop-unrolling
float dotProduct( float x[], float y[], int n )
{
   int n4= n/4*4; // or n4=n&(~3);
   float p=0;
   int i;

   for (i=0; i<n4; i+=4)
   {
      p+=x[i]*y[i];
      p+=x[i+1]*y[i+1];
      p+=x[i+2]*y[i+2];
      p+=x[i+3]*y[i+3];
   }

   // last n%4 elements
   for (; i<n; i++)
      p+=x[i]*y[i];

   return p;
}
```

La principal ventaja de esta optimización es que reduce el número de bifurcaciones condicionales de bucle en 75%. Además, al aumentar el número de operaciones en el cuerpo del bucle, el compilador puede tener más oportunidades de optimizar aún más. Por ejemplo, puede llevar a cabo algunas FPUs la adición multiplicar en += p x [i] * y [i] al capturar simultáneamente los valores de x [i + 1] e y [i + 1] para su uso en el paso siguiente. Este tipo de optimización es perfectamente seguro para operaciones de punto flotante porque conserva el orden de las operaciones.

A menudo resulta una ventaja para el compilador reordenar las operaciones de todas con el fin de generar un código más rápido. Observe el código siguiente:

```cpp
double a, b, c, d;
double x, y, z;
...
x = a*a*a + b*b*b + c*c*c;
...
y = a*a + b*b + c*c;
...
z = a + b + c;
```

Reglas semánticas de C++ indican que el programa debería producir resultados como si se ha calculado en primer lugar x, a continuación y, por último, z. Suponga que el compilador tiene solo cuatro registros de punto flotante disponibles. Si el compilador está obligado a proceso x, y y z en orden, puede elegir generar el código con la semántica siguiente:

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute x
r0 = a;         // r1 = a*a*a
r1 = r0*r0;
r1 = r1*r0;
r0 = b;         // r2 = b*b*b
r2 = r0*r0;
r2 = r2*r0;
r0 = c;         // r3 = c*c*c
r3 = r0*r0;
r3 = r3*r0;
r0 = r1 + r2;
r0 = r0 + r3;
x = r0;         // x = r1+r2+r3
// . . .
// Compute y
r0 = a;         // r1 = a*a
r1 = r0*r0;
r0 = b;         // r2 = b*b
r2 = r0*r0;
r0 = c;         // r3 = c*c
r3 = r0*r0;
r0 = r1 + r2;
r0 = r0 + r3;
y = r0;         // y = r1+r2+r3
// . . .
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1 + r2;
r0 = r0 + r3;
z = r0;         // z = r1+r2+r3
```

Hay varias operaciones claramente redundantes es esta codificación. Si el compilador sigue estrictamente reglas semánticas de C++, esta ordenación es necesaria porque el programa podría acceder el entorno de FPU entre cada asignación. Sin embargo, la configuración predeterminada para fp: precisa permiten al compilador optimizar como si el programa no tener acceso al entorno, lo que le permite volver a ordenar estas expresiones. A continuación, es libre de eliminarse el redundancias mediante el cálculo de los tres valores en orden inverso, como sigue:

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1+r2;
r0 = r0+r3;
z = r0;
...
// Compute y
r1 = r1*r1;
r2 = r2*r2;
r3 = r3*r3;
r0 = r1+r2;
r0 = r0+r3;
y = r0;
...
// Compute x
r0 = a;
r1 = r1*r0;
r0 = b;
r2 = r2*r0;
r0 = c;
r3 = r3*r0;
r0 = r1+r2;
r0 = r0+r3;
x = r0;
```

Esta codificación es claramente superior, tener reduce el número de instrucciones fp casi 40 por ciento. Los resultados de x, y y z son los mismos que antes, pero se calculan con menos sobrecarga.

Bajo fp: precisa, el compilador también puede *entrelazado* subexpresiones comunes con el fin de generar un código más rápido. Por ejemplo, el código para calcular las raíces de una ecuación cuadrática puede escribirse como sigue:

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

Aunque estas expresiones solo difieren en una sola operación, el programador puede haberla escrito esta forma de garantizar que cada valor de raíz se calcula en la mayor precisión resulta muy práctica. Bajo fp: precisa, el compilador es libre de entrelazado el cálculo de root0 y root1 quitar subexpresiones comunes sin perder precisión. Por ejemplo, la siguiente quitó varios pasos redundantes cuando se genera la misma respuesta exacta.

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

Otras optimizaciones pueden intentar mover la evaluación de algunas expresiones independientes. Tenga en cuenta el siguiente algoritmo que contiene una bifurcación condicional dentro de un cuerpo del bucle.

```cpp
vector<double> a(n);
double d, s;
// . . .
for (int i=0; i<n; i++)
{
   if (abs(d)>1.0)
      s = s+a[i]/d;
   else
      s = s+a[i]*d;
}
```

El compilador puede detectar que el valor de la expresión (abs(d) > 1) es invariable en el cuerpo del bucle. Esto permite al compilador para "elevar" if instrucción fuera del cuerpo del bucle, transformar el código anterior en lo siguiente:

```cpp
vector<double> a(n);
double d, s;
// . . .
if (abs(d)>1.0)
   for (int i=0; i<n; i++)
      s = s+a[i]/d;
else
   for (int i=0; i<n; i++)
      s = s+a[i]*d;
```

Después de la transformación, ya no es una bifurcación condicional en cualquiera de los cuerpos de bucle, lo que mejora significativamente el rendimiento general del bucle. Este tipo de optimización es perfectamente seguro porque la evaluación de la expresión (abs(d) > 1.0) es independiente de otras expresiones.

En presencia de acceso de entorno FPU o excepciones de punto flotante, estos tipos de optimización se contraindicado porque éstos cambien el flujo de semántica. Estas optimizaciones solo están disponibles en el fp: modo preciso porque una semántica de excepciones de punto flotante y acceso de entorno FPU está deshabilitada de forma predeterminada. Las funciones que tener acceso al entorno de FPU pueden deshabilitar explícitamente estas optimizaciones mediante el `fenv_access` pragma de compilador. Del mismo modo, deben usar las funciones mediante excepciones de punto flotante del `float_control(except ... )` compilador pragma (o usar el **/fp: excepto** conmutador de línea de comandos).

En resumen, fp: modo preciso permite que el compilador para volver a ordenar la evaluación de expresiones de punto flotante a condición de que no se modifican los resultados finales y que los resultados no son dependientes en el entorno de FPU o en excepciones de punto flotante.

### <a name="fpu-environment-access-under-fpprecise"></a>Acceso de entorno de FPU bajo fp: precisa

Cuando el fp: modo preciso está habilitado, el compilador supone que un programa no tener acceso o modificar el entorno de FPU. Como se mencionó anteriormente, esta suposición permite al compilador reorganizar o mover operaciones de punto flotante para mejorar la eficacia en fp: precisa.

Algunos programas pueden modificar el redondeo dirección punto flotante mediante el uso de la `_controlfp` (función). Por ejemplo, algunos programas de proceso superior y los límites inferiores de error en las operaciones aritméticas realizando el mismo cálculo dos veces, en primer lugar al redondeo a infinito negativo, a continuación, mientras redondeo a infinito positivo. Puesto que la FPU proporciona una manera cómoda de controlar el redondeo, un programador puede optar por cambiar modo de redondeo modificando el entorno de FPU. El código siguiente calcula el que error exacto enlazado de una multiplicación de punto flotante mediante la modificación del entorno FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Bajo fp: precisa, el compilador siempre se da por supuesto el entorno de FPU predeterminado, por lo que el optimizador es libre de omitir las llamadas a `_controlfp` y reducir las asignaciones anteriores a cUpper = cLower = un * b; esto claramente obtendrían resultados incorrectos. Para evitar estas optimizaciones, habilitar el acceso de entorno de FPU utilizando el `fenv_access` pragma de compilador.

Otros programas pueden intentar detectar algunos errores de punto flotante mediante la comprobación de palabra de estado de la FPU. Por ejemplo, el código siguiente comprueba las condiciones de división por cero e inexactos

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = r;
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

Bajo fp: precisa, las optimizaciones que volver a ordenar la evaluación de expresiones pueden cambiar los puntos en el que se producen algunos errores. Programas que se obtiene acceso a la palabra de estado deben habilitar el acceso de entorno de FPU utilizando el `fenv_access` pragma de compilador.

Para obtener más información, vea la sección [el pragma fenv_access](#the-fenv-access-pragma).

### <a name="floating-point-exception-semantics-under-fpprecise"></a>Semántica de excepciones de punto flotante en fp: precisa

De forma predeterminada, se deshabilita la semántica de excepciones de punto flotante en fp: precisa. La mayoría de los programadores de C++ prefieren controlar condiciones excepcionales de punto flotante sin usar las excepciones de C++ o del sistema. Además, como se mencionó anteriormente, deshabilitar la semántica de excepciones de punto flotante permite la mayor flexibilidad de compilador al optimizar las operaciones de punto flotante. Usar el **/fp: excepto** cambiar o `float_control` pragma para habilitar la semántica de excepciones de punto flotante cuando se usa el fp: modelo preciso.

Para obtener más información, vea la sección [habilitar la semántica de excepciones de punto flotante](#enabling-floating-point-exception-semantics).

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>El modo fp: Fast para la semántica de punto flotante

Cuando se habilita el modo de FP, el compilador relaja las reglas que fp: usa precisa al optimizar las operaciones de punto flotante. Este modo es que permite que el compilador optimizar aún más el código de punto flotante para acelerar el proceso a costa de precisión de punto flotante y la exactitud. Programas que no dependen de alta precisión cálculos de punto flotante pueden experimentar una mejora significativa velocidad habilitando el modo fp: Fast.

El modo de punto flotante fp: Fast se habilita mediante la [/fp: Fast](fp-specify-floating-point-behavior.md) modificador del compilador de línea de comandos como se indica a continuación:

> CL/fp: Fast source.cpp

En este ejemplo se indica al compilador que utilizan la semántica de FP al generar código para el archivo source.cpp. El modelo FP también se puede invocar en una función por función utilizando la `float_control` pragma de compilador.

Para obtener más información, vea la sección [la pragma float_control](#the-float-control-pragma).

En el modo FP, el compilador puede realizar las optimizaciones que modificar la precisión de los cálculos de punto flotante. El compilador no puede redondeo correctamente en las asignaciones, conversiones de tipo o llamadas a funciones y redondeo intermedios no siempre se realizará. Punto flotante optimizaciones específicas, como las contracciones, siempre están habilitadas. Semántica de excepciones de punto flotante y sensibilidad de entorno FPU están deshabilitado y no está disponible.

|semántica de FP: Fast|Explicación
|-|-|
|Semántica de redondeo|Redondeo explícita en las asignaciones, conversiones de tipo y se pueden omitir las llamadas a funciones.<br/>Expresiones intermedias se pueden redondear en menor que registrar precisión según los requisitos de rendimiento.|
|Transformaciones algebraicas|El compilador puede transformar expresiones según el número real asociativa, distributivo álgebra; no se garantiza que estas transformaciones sea exacto o correcto.|
|Contracciones|Siempre está habilitado; no se puede deshabilitar mediante la directiva pragma `fp_contract`|
|Orden de evaluación de punto flotante|El compilador puede reordenar la evaluación de expresiones de punto flotante, incluso cuando estos cambios pueden modificar los resultados finales.|
|Acceso de entorno FPU|Deshabilitado. No disponible|
|Semántica de excepciones de punto flotante|Deshabilitado. No disponible|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>Redondeo semántica para las expresiones de punto flotante en fp: Fast

A diferencia de fp: modelo preciso, el modelo fp: Fast realiza los cálculos intermedios precisión más cómodo. Redondeo en asignaciones, conversiones de tipo y llamadas a funciones no pueden producir siempre. Por ejemplo, la primera función a continuación presenta tres variables de precisión sencilla (`C`, `Y` y `T`). El compilador puede optar por registre estas variables, en vigor de la promoción de tipo `C`, `Y` y `T` a precisión doble.

Función original:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Registren de variables:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

En este ejemplo, fp: Fast ha trastocado la intención de la función original. La última optimizado resultado, que se mantienen en la variable `sum`, puede ser bastante perturbed desde el resultado correcto.

Bajo fp, el compilador intentará normalmente para mantener al menos la precisión especificada por el código fuente. Sin embargo, en algunos casos el compilador quizá prefiera realizar expresiones intermedias en un *menor precisión* que los especificados en el código fuente. Por ejemplo, el primer bloque de código siguiente llama a una versión de doble precisión de la función de raíz cuadrada. Bajo fp: Fast, en determinadas circunstancias, por ejemplo, cuando los resultados y los operandos de la función se convierten explícitamente a una precisión simple, el compilador puede elegir reemplazar la llamada a la precisión doble `sqrt` con una llamada a una precisión simple `sqrtf`(función). Dado que las conversiones Asegúrese de que el valor que se va a `sqrt` y el valor de salida se redondean a precisión sencilla, esto solo cambia el lugar de redondeo. Si el valor entran sqrt era un valor de precisión doble y el compilador realiza esta transformación, como máximo la mitad de los bits de precisión podría ser incorrecta.

Función original

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

Función optimizada

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
double tmp0 = a*a + b*b + c*c;
float tmp1 = tmp0;    // round of parameter value
float length = sqrtf(tmp1); // rounded sqrt result
float sum = f1 + f2;
```

Aunque menos preciso que esta optimización puede ser especialmente útil cuando se destinan a procesadores que proporcionan versiones intrínsecas de funciones de precisión simple como `sqrt`. Solo con precisión cuando el compilador usará estas optimizaciones es dependiente de la plataforma y el contexto.

Además, no hay ningún consistencia garantizada para la precisión de los cálculos intermedios, que se pueden realizar en cualquier nivel de precisión disponible para el compilador. Aunque el compilador intentará para mantener al menos el nivel de precisión según lo especificado por el código, fp: Fast permite al optimizador downcast cálculos intermedios para generar código máquina más rápida o más pequeño. Por ejemplo, el compilador puede optimizar aún más el código anterior para redondear algunas de las multiplicaciones intermedias a precisión sencilla.

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
float tmp0 = a*a;     // round intermediate a*a to single-precision
float tmp1 = b*b;     // round intermediate b*b to single-precision
double tmp2 = c*c;    // do NOT round intermediate c*c to single-precision
float tmp3 = tmp0 + tmp1 + tmp2;
float length = sqrtf(tmp3);
float sum = f1 + f2;
```

Este tipo de redondeo adicionales puede deberse al uso de una unidad punto flotante menor de precisión, como SSE2, para realizar algunas de los cálculos intermedios. La precisión de redondeo fp: Fast es, por tanto, depende de la plataforma; código que se compila correctamente para un procesador necesariamente podría no funcionar bien para otro procesador. Se deja al usuario para determinar si las ventajas de velocidad compensan los problemas de precisión.

Si la optimización fp: Fast es especialmente problemática para una función determinada, se puede cambiar el modo de punto flotante localmente a fp: precisa utilizando el `float_control` pragma de compilador.


### <a name="algebraic-transformations-under-fpfast"></a>Transformaciones algebraicas bajo fp: Fast

El modo fp: Fast permite al compilador realizar ciertas transformaciones algebraicas unsafe a flotante punto expresiones. Por ejemplo, se pueden emplear las siguientes optimizaciones no seguras en fp: Fast.

||||
|-|-|-|
|Código original|Paso 1 de #|Paso 2 de #
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

En el paso 1, el compilador observa que `z = y – a – b` siempre es igual a cero. Aunque esto es técnicamente una observación no válida, se permite en fp: Fast. El compilador, a continuación, propaga el valor constante cero para cada uso posterior de la variable z. En el paso 2, se optimiza el compilador aún más mediante la observación de que `x - 0 == x`, `x * 0 == 0`, etcetera. Una vez más, aunque estas observaciones no son estrictamente válidas, se permiten en fp: Fast. El código optimizado ahora es mucho más rápido, pero también puede ser considerablemente menor precisión o incluso incorrecto.

Cualquiera de las siguientes reglas algebraicas (no seguras) se puede emplear el optimizador cuando está habilitado el modo de FP:

|||
|-|-|
|Form|Descripción|
|`(a + b) + c = a + (b + c)`|Regla asociativa para adición|
|`(a * b) * c = a * (b * c)`|Regla asociativa de multiplicación|
|`a * (b + c) = a * b + b * c`|Distribución de multiplicación sobre la suma|
|`(a + b)(a - b) = a * a - b * b`|Factorización algebraico|
|`a / b = a * (1 / b)`|División por inverso multiplicativo|
|`a * 1.0 = a, a / 1.0 = a`|Identidad de multiplicación|
|`a ± 0.0 = a, 0.0 - a = -a`|Identidad aditiva|
|`a / a = 1.0, a - a = 0.0`|Cancelación|

Si la optimización fp: Fast es especialmente problemática para una función determinada, se puede cambiar el modo de punto flotante localmente a fp: precisa utilizando el `float_control` pragma de compilador.

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>Orden de evaluación de expresión de punto flotante en fp: Fast

A diferencia de fp: precisa, fp: Fast permite que el compilador reordenar las operaciones de punto flotante con el fin de generar un código más rápido. Por lo tanto, algunas optimizaciones en fp: Fast no pueden conservar el orden deseado de las expresiones. Por ejemplo, considere la siguiente función que calcula el producto escalar de dos vectores de n dimensiones.

```cpp
float dotProduct( float x[], float y[],
                  int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Bajo fp, el optimizador puede realizar una reducción escalar de la `dotProduct` funcione eficazmente transformar la función como sigue:

```cpp
float dotProduct( float x[], float y[],int n )
{
    int n4= n/4*4; // or n4=n&(~3);
    float p=0, p2=0, p3=0, p4=0;
    int i;

    for (i=0; i<n4; i+=4)
    {
        p+=x[i]*y[i];
        p2+=x[i+1]*y[i+1];
        p3+=x[i+2]*y[i+2];
        p4+=x[i+3]*y[i+3];
    }
    p+=p2+p3+p4;

    // last n%4 elements
    for (; i<n; i++)
    p+=x[i]*y[i];

    return p;
}
```

En la versión optimizada de la función cuatro producto independientes-sumas son realizadas al mismo tiempo y, a continuación, se suman. Esta optimización puede acelerar el cálculo de la `dotProduct` por tanto como un factor de cuatro según el procesador de destino, pero el resultado final puede ser tan incorrectos en cuanto a hacerla inservible. Si estas optimizaciones son especialmente problemáticas para función única o unidad de traducción, se puede cambiar el modo de punto flotante localmente a fp: precisa utilizando el `float_control` pragma de compilador.

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp: strict modo para la semántica de punto flotante

Cuando fp: strict modo está habilitado, el compilador se adhiere a las mismas reglas que fp: usa precisa al optimizar las operaciones de punto flotante. Este modo también habilita la semántica de excepciones de punto flotante y sensibilidad en el entorno de FPU y deshabilita ciertas optimizaciones como las contracciones. Es el modo de funcionamiento más estricto.

Fp: strict modo de punto flotante se habilita mediante la [/fp: strict](fp-specify-floating-point-behavior.md) modificador del compilador de línea de comandos como se indica a continuación:

> / de CL fp: strict source.cpp

Este ejemplo indica al compilador que utilice fp: strict semántica al generar código para el archivo source.cpp. Fp: modelo estricto también se puede invocar en una función por función utilizando la `float_control` pragma de compilador.

Para obtener más información, vea la sección [la pragma float_control](#the-float-control-pragma).

En el fp: modo strict, el compilador nunca realiza las optimizaciones que perturb la precisión de los cálculos de punto flotante. El compilador siempre se redondeará correctamente en las asignaciones, conversiones de tipo y llamadas a funciones y redondeo intermedio constantemente realizará en la misma precisión tal y como se registra la FPU. La semántica de excepciones de punto flotante y sensibilidad de entorno FPU están habilitadas de forma predeterminada. Ciertas optimizaciones, como las contracciones, están deshabilitados porque el compilador no puede garantizar la exactitud en todos los casos.

|fp: strict semántica|Explicación|
|-|-|
|Semántica de redondeo|Redondeo explícita en las asignaciones, conversiones de tipo y función llama a<br/>Expresiones intermedias se evaluará en el registro de precisión.<br/>Igual que fp: precisa|
|Transformaciones algebraicas|Estricta observancia de álgebra de punto flotante no asociativa, no distributivas, a menos que una transformación se garantiza que siempre generan los mismos resultados.<br/>Igual que fp: precisa|
|Contracciones|Siempre deshabilitada|
|Orden de evaluación de punto flotante|El compilador no reordenará la evaluación de expresiones de punto flotante|
|Acceso de entorno FPU|Siempre habilitado.|
|Semántica de excepciones de punto flotante|Habilitado de manera predeterminada.|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>Semántica de excepciones de punto flotante en fp: strict

De forma predeterminada, se habilita la semántica de excepciones de punto flotante en fp: strict modelo. Para deshabilitar esta semántica, use la **/fp: excepto-** cambiar o introducir un `float_control(except, off)` pragma.

Para obtener más información, vea las secciones [habilitar la semántica de excepciones de punto flotante](#enabling-floating-point-exception-semantics) y [el Pragma float_control](#the-float-control-pragma).

## <a name="the-fenvaccess-pragma"></a>La directiva pragma fenv_access

Uso:

```cpp
#pragma fenv_access( [ on  | off ] )
```

El [fenv_access](../../preprocessor/fenv-access.md) pragma permite al compilador que realice ciertas optimizaciones que podrían trastocar FPU marca pruebas y los cambios de modo FPU. Cuando el estado de `fenv_access` está deshabilitado, el compilador puede suponer que los modos FPU predeterminados están en vigor y que no se han probado FPU marcas. De forma predeterminada, el acceso de entorno está deshabilitado para fp: modo preciso, aunque puede habilitarse explícitamente mediante esta directiva pragma. Bajo fp: strict, `fenv_access` siempre está habilitada y no se puede deshabilitar. Bajo fp: Fast, `fenv_access` siempre está deshabilitada y no se puede habilitar.

Como se describe en el fp: sección precisa, algunos programadores pueden modificar el punto flotante en la dirección de redondeo utilizando la `_controlfp` (función). Por ejemplo, para calcular los límites de error superior e inferior de las operaciones aritméticas, algunos programas realizan el mismo cálculo dos veces, en primer lugar al redondeo a infinito negativo y luego al redondeo a infinito positivo. Puesto que la FPU proporciona una manera cómoda de controlar el redondeo, un programador puede optar por cambiar modo de redondeo modificando el entorno de FPU. El código siguiente calcula el que error exacto enlazado de una multiplicación de punto flotante mediante la modificación del entorno FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Cuando está deshabilitado, el `fenv_access` pragma permite al compilador que suponga el entorno de FPU predeterminado; de este modo el optimizador libre para pasar por alto las llamadas a `_controlfp` y reducir las asignaciones anteriores a `cUpper = cLower = a*b`. Cuando se habilita, sin embargo, `fenv_access` evita estas optimizaciones.

Programas también pueden comprobar la palabra de estado de la FPU para detectar algunos errores de punto flotante. Por ejemplo, el código siguiente comprueba las condiciones de división por cero e inexactos

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

Cuando `fenv_access` está deshabilitado, el compilador puede reorganizar el orden de ejecución de las expresiones de punto flotante, lo que posiblemente subverting las comprobaciones de estado de la FPU. Habilitar `fenv_access` evita estas optimizaciones.

## <a name="the-fpcontract-pragma"></a>La directiva pragma fp_contract

Uso:

```cpp
#pragma fp_contract( [ on | off ] )
```

Como se describe en el fp: sección precisa, contracción es una característica de arquitectura fundamental para muchas unidades de punto flotante modernas. Contracciones proporcionan la capacidad para realizar una multiplicación seguida por una adición como una operación única con ningún error de redondeo intermedio. Estas instrucciones solo son más rápidas que la ejecución independiente multiplicar y agregar instrucciones y son más precisas porque no hay ningún redondeo intermedio del producto. Una operación contratada puede calcula el valor de `(a*b+c)` como si ambas operaciones se calculara como precisión infinita y, a continuación, se redondea con la más cercano de número de punto flotante. Esta optimización significativamente puede acelerar las funciones que contienen varios intercalar multiplicar y agregar las operaciones. Por ejemplo, considere el siguiente algoritmo que calcula el producto escalar de dos vectores de n dimensiones.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Este cálculo puede realizarse una serie de instrucciones del formulario multiplicar-agregar `p = p + x[i]*y[i]`.

El [fp_contract](../../preprocessor/fp-contract.md) pragma especifica si se pueden contraer expresiones de punto flotante. De forma predeterminada, el fp: modo preciso permite contracciones puesto que mejoran la precisión y la velocidad. Contracciones siempre están habilitadas para el modo fp: Fast. Sin embargo, dado que contracciones pueden trastocar la detección explícita de condiciones de error, el `fp_contract` pragma siempre está deshabilitada en el fp: modo strict. Ejemplos de expresiones que se pueden contraer cuando el `fp_contract` pragma está habilitado:

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

## <a name="the-floatcontrol-pragma"></a>El float_control (pragma)

El **/fp: precisa**, **/fp: Fast**, **/fp: strict** y **/fp: excepto** modificadores controlan la semántica de punto flotante en un archivo por archivo base. El [float_control](../../preprocessor/float-control.md) directiva pragma proporciona dicho control según una función por función.

Uso:

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Las directivas pragma `float_control(push)` y `float_control(pop)` respectivamente, insertar y extraer el estado actual del modo de punto flotante y la opción de excepción en una pila. Tenga en cuenta que el estado de la `fenv_access` y `fp_contract` pragma no se ven afectados por `pragma float_control(push/pop)`.

Una llamada a la directiva pragma `float_control(precise, on)` habilitará y `float_control(precise, off)` se deshabilitará la semántica de modo preciso. Del mismo modo, la directiva pragma `float_control(except, on)` habilitará y `float_control(except, off)` , se deshabilitará la semántica de excepciones. La semántica de excepciones sólo puede habilitarse cuando también se habilita la semántica precisa. Cuando la parte opcional `push` argumento está presente, los Estados de la `float_control` opciones se insertan antes de cambiar la semántica.

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>Establecer el modo de semántica de punto flotante en la función por función

Los modificadores de línea de comandos son en realidad abreviada para establecer las directivas pragma de punto flotante diferentes cuatro. Para elegir explícitamente un modo semántica punto flotante determinado según una función por función, seleccione cada una de las cuatro pragmas de opción de punto flotante como se describe en la tabla siguiente:

||||||
|-|-|-|-|-|
||float_control(precise)|float_control(except)|fp_contract|fenv_access|
|/ fp: strict|el|el|Desactivar|el|
|/ fp: strict/fp: excepto:|el|Desactivar|Desactivar|el|
|/ fp: precisa|el|Desactivar|el|Desactivar|
|/ fp: precisa/fp: excepto|el|el|el|Desactivar|
|/ fp: Fast|Desactivar|Desactivar|el|Desactivar|

Por ejemplo, la siguiente habilita explícitamente la semántica de FP: Fast.

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> La semántica de excepciones debe desactivarse antes de desactivar la semántica "precisa".

## <a name="enabling-floating-point-exception-semantics"></a>Habilitar la semántica de excepciones de punto flotante

Algunas condiciones de punto flotante excepcionales, como dividir por cero, pueden hacer que la FPU indicar una excepción de hardware. Excepciones de punto flotante se deshabilitan de forma predeterminada. Excepciones de punto flotante se habilitan mediante la modificación de la palabra de control FPU con el `_controlfp` función. Por ejemplo, el siguiente código habilita la excepción de punto flotante de división por cero:

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

Cuando se habilita la excepción de división por cero, cualquier operación de división cuyo denominador es igual a cero producirá una excepción de FPU a que se señalice.

Para restaurar la palabra de control FPU para el modo predeterminado, llame a `_controlfp(_CW_DEFAULT, ~0)`.

Habilitar la semántica de excepciones de punto flotante con el **/fp: excepto** marca no es el mismo que habilitar excepciones de punto flotante. Cuando se habilita la semántica de excepciones de punto flotante, el compilador debe tener en cuenta la posibilidad de que cualquier operación de punto flotante podría producir una excepción. Dado que la FPU es una unidad de procesador independiente, se pueden realizar las instrucciones que se ejecuta en la FPU simultáneamente con instrucciones en otras unidades.

Cuando se habilita una excepción de punto flotante, la FPU se detiene la ejecución de la instrucción del proceso causante del error y, a continuación, se indican una condición excepcional estableciendo la palabra de estado de la FPU. Cuando la CPU alcanza la siguiente instrucción de punto flotante, primero se comprueba para las excepciones de FPU pendientes. Si se produce una excepción pendiente, el procesador de captura mediante una llamada a un controlador de excepción proporcionado por el sistema operativo. Esto significa que cuando una operación de punto flotante encuentra una condición excepcional, no se ha detectado la excepción correspondiente hasta que se ejecute la siguiente operación de punto flotante. Por ejemplo, el siguiente código intercepta una excepción de división por cero:

```cpp
double a, b, c;
// . . .
// ...unmasking of FPU exceptions omitted...
__try
{
   b/c; // assume c==0.0
   printf("This line shouldn't be reached when c==0.0\n");
   c = 2.0*b;
}
__except( EXCEPTION_EXECUTE_HANDLER )
{
   printf("SEH Exception Detected\n");
}
// . . .
```

Si se produce una condición de división por cero en la expresión un = b y c, la FPU no captura/generar la excepción hasta la siguiente operación de punto flotante en la expresión 2.0 * b. Esto genera el siguiente resultado:

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Las funciones intrínsecas printf correspondiente a la primera línea de la salida no debería haber ha alcanzado; se alcanzó porque no se produjo la excepción de punto flotante causada por la expresión, b y c hasta que llegue a ejecución 2.0 * b. Para generar la excepción después de ejecutar, b y c, el compilador debe introducir una instrucción "espera":

```cpp
// . . .
   __try
   {
      b/c; // assume this expression will cause a "divide-by-zero" exception
      __asm fwait;
      printf("This line shouldn't be reached when c==0.0\n");
      c = 2.0*b;
   }
// . . .
```

Esta instrucción "espera" fuerza el procesador para sincronizar con el estado de la FPU y controlar las excepciones pendientes. El compilador generará solo estos "espera" instrucciones cuando se habilita la semántica de punto flotante. Cuando esta semántica está deshabilitada, tal y como existen de forma predeterminada, los programas pueden producirse errores de sincronización, similares a la anterior, al usar excepciones de punto flotante.

Cuando se habilita la semántica de punto flotante, el compilador no incorporará solo las instrucciones de "espera", también impedirá que el compilador de forma no autorizada optimizar el código de punto flotante en presencia de posibles excepciones. Esto incluye las transformaciones que modifican los puntos en el que se produzcan excepciones. Debido a estos factores, habilitar la semántica de punto flotante puede reducir considerablemente la eficacia del código generado de máquina, por tanto, degradar el rendimiento de la aplicación.

La semántica de excepciones de punto flotante se habilita de forma predeterminada en fp: modo strict. Para habilitar esta semántica en fp: modo preciso, agregue el **/fp: excepto** cambiar para el compilador de línea de comandos. La semántica de excepciones de punto flotante puede también habilitar y deshabilitar según una función por función utilizando la `float_control` pragma.

### <a name="floating-point-exceptions-as-c-exceptions"></a>Excepciones de punto flotante como excepciones de C++

Como con todas las excepciones de hardware, excepciones de punto flotante no intrínsecamente provocarán una excepción de C++, pero en su lugar, desencadenan una excepción estructurada. Para asignar las excepciones estructuradas punto flotante a las excepciones de C++, los usuarios pueden introducir a un traductor de excepciones de SEH personalizado. En primer lugar, introduce una excepción de C++ correspondiente a cada excepción de punto flotante:

```cpp
class float_exception : public std::exception {};

class fe_denormal_operand : public float_exception {};
class fe_divide_by_zero : public float_exception {};
class fe_inexact_result : public float_exception {};
class fe_invalid_operation : public float_exception {};
class fe_overflow : public float_exception {};
class fe_stack_check : public float_exception {};
class fe_underflow : public float_exception {};
```

A continuación, introduzca una función de traducción que detectará una excepción SEH punto flotante y producir la excepción de C++ correspondiente. Para usar esta función, establezca el traductor de controlador de excepciones estructurado para el subproceso actual con la [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) función de la biblioteca en tiempo de ejecución.

```cpp
void se_fe_trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )
{
    switch (u)
    {
    case STATUS_FLOAT_DENORMAL_OPERAND:   throw fe_denormal_operand();
    case STATUS_FLOAT_DIVIDE_BY_ZERO:     throw fe_divide_by_zero();
   etc...
    };
}
// . . .
_set_se_translator(se_fe_trans_func);
```

Una vez que se inicializa esta asignación, excepciones de punto flotante se comportarán como si fueran las excepciones de C++. Por ejemplo:

```cpp
try
{
   // floating-point code that might throw divide-by-zero
   // or other floating-point exception
}
catch(fe_divide_by_zero)
{
    cout << "fe_divide_by_zero exception detected" << endl;
}
catch(float_exception)
{
    cout << "float_exception exception detected" << endl;
}
```

## <a name="references"></a>Referencias

[Lo que cada equipo científico debería saber acerca de la aritmética de coma flotante](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf) por David Camilo.

## <a name="see-also"></a>Vea también

[Optimizar el código](optimizing-your-code.md)<br/>
