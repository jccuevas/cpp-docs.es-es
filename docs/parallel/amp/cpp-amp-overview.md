---
title: "Informaci&#243;n general sobre C++ AMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, requisitos"
  - "C++ Accelerated Massive Parallelism, arquitectura"
  - "C++ AMP"
  - "C++ Accelerated Massive Parallelism, información general"
  - "C++ Accelerated Massive Parallelism"
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
caps.latest.revision: 60
caps.handback.revision: 60
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general sobre C++ AMP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C++ Accelerated Massive Parallelism (C++ AMP) acelera la ejecución de código C++ aprovechando las ventajas de hardware paralelo de datos como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica independiente. Mediante C++ AMP, puede codificar los algoritmos de datos multidimensionales para que se puede acelerar la ejecución mediante el uso de paralelismo en hardware heterogénea. El modelo de programación de C++ AMP incluye matrices multidimensionales, indización, transferencia de memoria, segmentación y una biblioteca de funciones matemáticas. Puede usar las extensiones de lenguaje C++ AMP para controlar cómo se mueven los datos de la CPU a la GPU y viceversa, por lo que puede mejorar el rendimiento.  
  
## <a name="system-requirements"></a>Requisitos del sistema  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)] o [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)]  
  
-   DirectX 11 característica nivel 11.0 o posterior hardware  
  
-   Para depurar en el emulador de software, [!INCLUDE[win8](../../build/includes/win8_md.md)] o [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] es necesaria. Para depurar en el hardware, debe instalar los controladores de su tarjeta gráfica. Para obtener más información, consulte [Depurar código de GPU](../Topic/Debugging%20GPU%20Code.md).  
  
## <a name="introduction"></a>Introducción  
 Los dos ejemplos siguientes muestran los principales componentes de C++ AMP. Suponga que desea agregar los elementos correspondientes de dos matrices unidimensionales. Por ejemplo, desea agregar `{1, 2, 3, 4, 5}` y `{6, 7, 8, 9, 10}` para obtener `{7, 9, 11, 13, 15}`. Sin usar C++ AMP, puede escribir el siguiente código para sumar los números y mostrar los resultados.  
  
```cpp  
  
#include <iostream>  
  
void StandardMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
  
```  
  
 Las partes importantes del código son los siguientes:  
  
-   Datos: Los datos se componen de tres matrices. Todos tienen el mismo rango (uno) y longitud (cinco).  
  
-   Iteración: La primera `for` bucle proporciona un mecanismo para recorrer en iteración los elementos de las matrices. El código que desea ejecutar para calcular las sumas se encuentra en la primera `for` bloque.  
  
-   Índice: La `idx` variable tiene acceso a los elementos individuales de las matrices.  
  
 Usar C++ AMP, puede escribir el código siguiente en su lugar.  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
const int size = 5;  
  
void CppAmpMethod() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[size];  
  
    // Create C++ AMP objects.  
    array_view<const int, 1> a(size, aCPP);  
    array_view<const int, 1> b(size, bCPP);  
    array_view<int, 1> sum(size, sumCPP);  
    sum.discard_data();  
  
    parallel_for_each(   
        // Define the compute domain, which is the set of threads that are created.  
        sum.extent,   
        // Define the code to run on each thread on the accelerator.  
 [=](index<1> idx) restrict(amp)  
    {  
        sum[idx] = a[idx] + b[idx];  
    }  
    );  
  
    // Print the results. The expected output is "7, 9, 11, 13, 15".  
    for (int i = 0; i < size; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 Los mismos elementos básicos están presentes, pero se utilizan construcciones de C++ AMP:  
  
-   Datos: Usar matrices de C++ para construir tres C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) objetos. Se proporcionan cuatro valores para construir un `array_view` objeto: los valores de datos, el rango, el tipo de elemento y la longitud de la `array_view` objeto en cada dimensión. El rango y el tipo se pasan como parámetros de tipo. Los datos y la longitud se pasan como parámetros del constructor. En este ejemplo, la matriz de C++ que se pasa al constructor es unidimensional. El rango y longitud que se utilizan para construir la forma rectangular de los datos de la `array_view` objeto y los valores se utilizan para rellenar la matriz de datos. La biblioteca en tiempo de ejecución también incluye el [array (clase)](../../parallel/amp/reference/array-class.md), que tiene una interfaz similar a la `array_view` de clase y se describe más adelante en este artículo.  
  
-   Iteración: El [parallel_for_each (función) (C++ AMP)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) proporciona un mecanismo para recorrer en iteración los elementos de datos, o *compute dominio*. En este ejemplo, se especifica el dominio de cálculo por `sum.extent`. El código que desea ejecutar está contenido en una expresión lambda, o *función de kernel*. La `restrict(amp)` indica que se usa sólo el subconjunto del lenguaje C++ que C++ AMP pueda acelerar.  
  
-   Índice: La [index (clase)](../../parallel/amp/reference/index-class.md) variable, `idx`, se declara con un rango de uno para que coincida con el rango de la `array_view` objeto. Mediante el índice, puede tener acceso a los elementos individuales de la `array_view` objetos.  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>Datos de formas y la indización: índice y la extensión  
 Debe definir los valores de datos y declarar la forma de los datos antes de ejecutar el código de kernel. Todos los datos se define como una matriz (rectangular) y puede definir la matriz para que cualquier rango (número de dimensiones). Los datos pueden ser de cualquier tamaño en cualquiera de las dimensiones.  
  
### <a name="index-class"></a>index (Clase)  
 El [index (clase)](../../parallel/amp/reference/index-class.md) especifica una ubicación en la `array` o `array_view` objeto encapsulando el desplazamiento desde el origen de cada dimensión en un objeto. Para obtener acceso a una ubicación en la matriz, se pasa un `index` objeto para el operador de indización, `[]`, en lugar de una lista de los índices de entero. Puede tener acceso a los elementos de cada dimensión utilizando el [array::operator() (operador)](../Topic/array::operator\(\)%20Operator.md) o [array_view::operator() () (operador)](../Topic/array_view::operator\(\)%20Operator.md).  
  
 En el ejemplo siguiente se crea un índice unidimensional que especifica el tercer elemento unidimensional `array_view` objeto. El índice se utiliza para imprimir el tercer elemento de la `array_view` objeto. El resultado es 3.  
  
```cpp  
 
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout <<a[idx] <<"\n";    
// Output: 3  
 
```  
  
 En el ejemplo siguiente se crea un índice bidimensional que especifica el elemento donde la fila = 1 y la columna 2 en un bidimensional `array_view` objeto. El primer parámetro de la `index` constructor es el componente de fila y el segundo parámetro es el componente de columna. El resultado es 6.  
  
```cpp  
 
int aCPP[] = {1, 2, 3,  
    4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] <<"\n";  
// Output: 6  
 
```  
  
 En el ejemplo siguiente se crea un índice tridimensional que especifica el elemento donde la profundidad = 0, la fila = 1 y la columna = 3 en tridimensional `array_view` objeto. Observe que el primer parámetro es el componente de profundidad, el segundo parámetro es el componente de fila y el tercer parámetro es el componente de columna. El resultado es 8.  
  
```cpp  
 
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
 
array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.  
index<3> idx(0, 1, 3);

std::cout <<a[idx] <<"\n";  
 
// Output: 8  
 
```  
  
### <a name="extent-class"></a>extent (Clase)  
 El [extent (clase)](../../parallel/amp/reference/extent-class-cpp-amp.md) especifica la longitud de los datos en cada dimensión de la `array` o `array_view` objeto. Puede crear una extensión y usarlo para crear un `array` o `array_view` objeto. También puede recuperar el alcance de un miembro de `array` o `array_view` objeto. En el ejemplo siguiente se imprime la longitud de la extensión de cada dimensión de una `array_view` objeto.  
  
```cpp  
 
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
// There are 3 rows and 4 columns, and the depth is two.  
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout <<"The number of columns is " <<a.extent[2] <<"\n";  
std::cout <<"The number of rows is " <<a.extent[1] <<"\n";  
std::cout <<"The depth is " <<a.extent[0]<<"\n";  
std::cout <<"Length in most significant dimension is " <<a.extent[0] <<"\n";  
 
```  
  
 En el ejemplo siguiente se crea un `array_view` dimensiones de objeto que tiene el mismo que el objeto en el ejemplo anterior, pero en este ejemplo usa un `extent` objeto en lugar de utilizar parámetros explícitos en el `array_view` constructor.  
  
```cpp  
 
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout <<"The number of columns is " <<a.extent[2] <<"\n";  
std::cout <<"The number of rows is " <<a.extent[1] <<"\n";  
std::cout <<"The depth is " <<a.extent[0] <<"\n";  
 
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Movimiento de datos para el Acelerador de: array y array_view  
 Dos contenedores de datos que se usa para mover datos en el Acelerador se definen en la biblioteca en tiempo de ejecución. Son el [array (clase)](../../parallel/amp/reference/array-class.md) y [array_view (clase)](../../parallel/amp/reference/array-view-class.md). El `array` es una clase de contenedor que crea una copia en profundidad de los datos cuando se construye el objeto. La `array_view` clase es una clase contenedora que copia los datos cuando la función de kernel tiene acceso a los datos. Cuando se necesitan los datos en el dispositivo de origen los datos se copian de nuevo.  
  
### <a name="array-class"></a>array (Clase)  
 Cuando un `array` se construye el objeto, se crea una copia en profundidad de los datos en el acelerador si utiliza un constructor que incluye un puntero al conjunto de datos. La función de kernel modifica la copia en el acelerador. Cuando finaliza la ejecución de la función de kernel, debe copiar los datos a la estructura de datos de origen. En el ejemplo siguiente se multiplica cada elemento de un vector por 10. Una vez finalizada la función de kernel, el [operador de conversión de vector--] brokenlink--(.. /Topic/Array::operator%20std::vector%3Cvalue_type%3E%20Operator.MD)is usa para copiar los datos en el objeto de vector.  
  
```cpp  
 
std::vector<int> data(5);

for (int count = 0; count <5; count++)   
{  
    data[count] = count;  
}  
 
array<int, 1> a(5, data.begin(), data.end());

 
parallel_for_each(
    a.extent, 
 [=, &a](index<1> idx) restrict(amp)  
 {  
    a[idx] = a[idx]* 10;  
 });

 
data = a;  
for (int i = 0; i <5; i++)   
{  
    std::cout <<data[i] <<"\n";  
}  
 
```  
  
### <a name="arrayview-class"></a>array_view (Clase)  
 El `array_view` tiene prácticamente los mismos miembros que la `array` clase, pero el comportamiento subyacente no es el mismo. Los datos pasan a la `array_view` constructor no se replica en la GPU como lo es con un `array` constructor. En su lugar, los datos se copian en el acelerador cuando se ejecuta la función de kernel. Por lo tanto, si crea dos `array_view` objetos que usan los mismos datos, ambos `array_view` objetos hacen referencia al mismo espacio de memoria. Al hacer esto, tendrá que sincronizar el acceso multiproceso. La principal ventaja de utilizar el `array_view` clase es que se mueven los datos sólo si es necesario.  
  
### <a name="comparison-of-array-and-arrayview"></a>Comparación de matriz y array_view  
 En la tabla siguiente se resumen las similitudes y diferencias entre el `array` y `array_view` clases.  
  
|Descripción|array (clase)|array_view (clase)|  
|-----------------|-----------------|-----------------------|  
|Cuando se determine el rango|En tiempo de compilación.|En tiempo de compilación.|  
|Cuando se determina la extensión|En tiempo de ejecución.|En tiempo de ejecución.|  
|Forma|Rectangular.|Rectangular.|  
|Almacenamiento de datos|Es un contenedor de datos.|Es un contenedor de datos.|  
|Copiar|Copia explícita y profunda en la definición.|Copia implícita cuando se tiene acceso mediante la función de kernel.|  
|Recuperación de datos|Copiando datos de la matriz a un objeto en el subproceso de CPU.|Mediante el acceso directo de la `array_view` del objeto o al llamar a la [array_view:: Synchronize (método)](../Topic/array_view::synchronize%20Method.md) para continuar accediendo a los datos en el contenedor original.|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>Memoria compartida con la matriz y array_view  
 Memoria compartida es que puede tener acceso por la CPU y el acelerador. El uso de memoria compartida se elimina o reduce la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria se comparte, no se puede tener acceso simultáneamente a la CPU y el acelerador y al hacerlo provoca un comportamiento indefinido.  
  
 `array` objetos pueden utilizarse para especificar un mayor control sobre el uso de memoria compartida si lo admite el Acelerador asociado. Si un acelerador es compatible con memoria compartida está determinado por el Acelerador [supports_cpu_shared_memory](../Topic/accelerator::supports_cpu_shared_memory%20Data%20Member.md) propiedad que devuelve `true` cuando se admite la memoria compartida. Si se admite la memoria compartida, el valor predeterminado [access_type (enumeración)](../Topic/access_type%20Enumeration.md) memoria asignaciones en el Acelerador se determina mediante el `default_cpu_access_type` propiedad. De forma predeterminada, `array` y `array_view` objetos adoptan el mismo `access_type` como el principal asociado `accelerator`.  
  
 Estableciendo el [array::cpu_access_type miembro de datos](../Topic/array::cpu_access_type%20Data%20Member.md) propiedad de un `array` explícitamente, puede ejercicio específico controlar en la memoria compartida de cómo se utiliza, puede optimizar la aplicación para las características de rendimiento del hardware, según los patrones de acceso de la memoria del kernel de su cálculo. Un `array_view` refleja el mismo `cpu_access_type` como el `array` que está asociado; o bien, si se construye el array_view sin un origen de datos, su `access_type` refleja el entorno que hace asignar el almacenamiento. Es decir, si primero se obtiene acceso por el host (CPU), se comporta como si se hubiera creado sobre un origen de datos de la CPU y recursos compartidos de la `access_type` de la `accelerator_view` asociada captura; sin embargo, si es el primero acceso a un `accelerator_view`, a continuación, se comporta como si se hubiera creado sobre un `array` creado en el que `accelerator_view` y comparte el `array`del `access_type`.  
  
 En el ejemplo de código siguiente se muestra cómo determinar si el Acelerador predeterminado es compatible con memoria compartida y, a continuación, crea varias matrices que tienen configuraciones diferentes cpu_access_type.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
  accelerator acc = accelerator(accelerator::default_accelerator);  
  
  // Early out if the default accelerator doesn’t support shared memory.  
  if (!acc.supports_cpu_shared_memory)  
  {  
    std::cout << "The default accelerator does not support shared memory" << std::endl;  
    return 1;  
  }  
  
  // Override the default CPU access type.  
  acc.default_cpu_access_type = access_type_read_write  
  
  // Create an accelerator_view from the default accelerator. The  
  // accelerator_view inherits its default_cpu_access_type from acc.  
  accelerator_view acc_v = acc.default_view;  
  
  // Create an extent object to size the arrays.  
  extent<1> ex(10);  
  
  // Input array that can be written on the CPU.  
  array<int, 1> arr_w(ex, acc_v, access_type_write);  
  
  // Output array that can be read on the CPU.  
  array<int, 1> arr_r(ex, acc_v, access_type_read);  
  
  // Read-write array that can be both written to and read from on the CPU.  
  array<int, 1> arr_rw(ex, acc_v, access_type_read_write);  
}  
  
```  
  
## <a name="executing-code-over-data-parallelforeach"></a>Ejecución de código sobre datos: parallel_for_each  
 El [parallel_for_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) función define el código que desea ejecutar en el Acelerador contra los datos de la `array` o `array_view` objeto. Considere el siguiente código desde la introducción de este tema.  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddArrays() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
 [=](index<1> idx) restrict(amp)  
        {  
            sum[idx] = a[idx] + b[idx];  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 El `parallel_for_each` método toma dos argumentos, un dominio de cálculo y una expresión lambda.  
  
 El *compute dominio* es un `extent` objeto o un `tiled_extent` objeto que define el conjunto de subprocesos se pueden crear para la ejecución en paralelo. Se genera un subproceso para cada elemento en el dominio de cálculo. En este caso, el `extent` objeto es unidimensional y tiene cinco elementos. Por lo tanto, se inician cinco subprocesos.  
  
 El *expresión lambda* define el código para ejecutarse en cada subproceso. La cláusula capture, `[=]`, especifica que el cuerpo de la expresión lambda tiene acceso a todas las variables capturadas por valor, que en este caso son `a`, `b`, y `sum`. En este ejemplo, la lista de parámetros crea una unidimensional `index` variable denominada `idx`. El valor de la `idx[0]` es 0 en el primer subproceso y se incrementa en uno en cada subproceso subsiguientes. La `restrict(amp)` indica que se usa sólo el subconjunto del lenguaje C++ que C++ AMP pueda acelerar.  Se describen las limitaciones de las funciones que tienen el modificador restringir en [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md). Para obtener más información, consulte, [sintaxis de expresiones Lambda](../../cpp/lambda-expression-syntax.md).  
  
 La expresión lambda puede incluir el código para ejecutar o puede llamar a una función de kernel independiente. La función de kernel debe incluir el `restrict(amp)` modificador. El ejemplo siguiente es equivalente al ejemplo anterior, pero llama a una función de kernel independiente.  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddElements(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)  
{  
    sum[idx] = a[idx] + b[idx];  
}  
  
void AddArraysWithFunction() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
 [=](index<1> idx) restrict(amp)  
        {  
            AddElements(idx, sum, a, b);  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
## <a name="accelerating-code-tiles-and-barriers"></a>Acelerada código: Los iconos y las barreras  
 Puede tener más aceleración mediante mosaico. Mosaico divide los subprocesos en subconjuntos rectangulares iguales o *mosaicos*. Determinar el tamaño del mosaico adecuado basado en el conjunto de datos y el algoritmo de codificación. Para cada subproceso tiene acceso a la *global* ubicación de un elemento de datos en relación con toda la `array` o `array_view` y el acceso a la *local* ubicación concierne al mosaico. Con el valor de índice local simplifica el código porque no tiene que escribir el código para convertir valores de índice de global a local. Para utilizar la disposición en mosaico, llame a la [Extent:: Tile (método)](../Topic/extent::tile%20Method.md) en el dominio de cálculo en el `parallel_for_each` método y use un [tiled_index](../../parallel/amp/reference/tiled-index-class.md) objeto en la expresión lambda.  
  
 En las aplicaciones típicas, están relacionados con los elementos de un mosaico de alguna manera y el código tiene acceso y realizar un seguimiento de los valores en el mosaico. Use el [tile_static (palabra clave)](../../cpp/tile-static-keyword.md) (palabra clave) y el [tile_barrier método](../Topic/tile_barrier::wait%20Method.md) para lograr esto. Una variable que tiene el `tile_static` palabra clave tiene un ámbito en una ventana completa y se crea una instancia de la variable para cada mosaico. Debe controlar la sincronización de subproceso de mosaico tenga acceso a la variable. El [tile_barrier método](../Topic/tile_barrier::wait%20Method.md) detiene la ejecución del subproceso actual hasta que todos los subprocesos del mosaico alcancen la llamada a `tile_barrier::wait`. Por lo que se puede acumular valores entre el mosaico usando `tile_static` variables. A continuación, puede finalizar todos los cálculos que requieren acceso a todos los valores.  
  
 El siguiente diagrama representa una matriz bidimensional de muestreo de datos que se organizan en mosaico.  
  
 ![Valores de índice en una extensión en mosaico](../../parallel/amp/media/camptiledgridexample.png "CampTiledGridExample")  
  
 El ejemplo de código siguiente utiliza los datos de muestreo del diagrama anterior. El código sustituye cada valor en el mosaico por la media de los valores del mosaico.  
  
```cpp  
 
// Sample data:  
int sampledata[] = {  
    2, 2, 9, 7, 1, 4,  
    4, 4, 8, 8, 3, 4,  
    1, 5, 1, 2, 5, 2,  
    6, 8, 3, 2, 7, 2};  
 
// The tiles:  
// 2 2    9 7    1 4  
// 4 4    8 8    3 4  
//  
// 1 5    1 2    5 2  
// 6 8    3 2    7 2  
 
// Averages:  
int averagedata[] = {   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
};  
 
array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

 
parallel_for_each(*// Create threads for sample.extent and divide the extent into 2 x 2 tiles.  
    sample.extent.tile<2,2>(), 
 [=](tiled_index<2,2> idx) restrict(amp)  
 { *// Create a 2 x 2 array to hold the values in this tile.  
    tile_static int nums[2][2]; *// Copy the values for the tile into the 2 x 2 array.  
    nums[idx.local[1]][idx.local[0]] = sample[idx.global]; *// When all the threads have executed and the 2 x 2 array is complete, find the average.  
    idx.barrier.wait();
int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1]; *// Copy the average into the array_view.  
    average[idx.global] = sum / 4;  
 });

 
for (int i = 0; i <4; i++) {  
    for (int j = 0; j <6; j++) {  
    std::cout <<average(i,j) <<" ";  
 }  
    std::cout <<"\n";  
}  
 
// Output:  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
 
```  
  
## <a name="math-libraries"></a>Bibliotecas matemáticas  
 C++ AMP incluye dos bibliotecas matemáticas. La biblioteca de precisión doble en el [el espacio de nombres de precise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) proporciona compatibilidad para las funciones de precisión doble. También proporciona compatibilidad para las funciones de precisión sencilla, aunque sigue siendo necesaria la compatibilidad de doble precisión en el hardware. Cumple con el [especificación C99 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/LinkId=225887). El acelerador debe admitir completa de doble precisión. Puede determinar si realiza comprobando el valor de la [accelerator::supports_double_precision miembro de datos](../Topic/accelerator::supports_double_precision%20Data%20Member.md). La biblioteca matemática rápido, en la [el espacio de nombres de fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md), contiene otro conjunto de funciones matemáticas. Estas funciones, que solo admiten `float` operandos, ejecutar más rápidamente, pero no tan precisos como los de la biblioteca matemática de precisión doble. Las funciones se incluyen en el archivo de encabezado \< amp_math.h > y todos se declaran con `restrict(amp)`. Las funciones en el \< cmath> archivo de encabezado se importan en ambos el `fast_math` y `precise_math` los espacios de nombres. El `restrict` palabra clave se utiliza para distinguir el \< cmath> versión y la versión de C++ AMP. El código siguiente calcula el logaritmo en base 10, con el método rápido de cada valor que se encuentra en el dominio de cálculo.  
  
```cpp  
  
#include <amp.h>  
#include <amp_math.h>  
#include <iostream>  
using namespace concurrency;  
  
void MathExample() {  
  
    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };  
    array_view<double, 1> logs(6, numbers);  
  
    parallel_for_each(  
        logs.extent,  
 [=] (index<1> idx) restrict(amp) {  
            logs[idx] = concurrency::fast_math::log10(logs[idx]);  
        }  
    );  
  
    for (int i = 0; i < 6; i++) {  
        std::cout << logs[i] << "\n";  
    }  
}  
  
```  
  
## <a name="graphics-library"></a>Biblioteca gráfica  
 C++ AMP incluye una biblioteca de gráficos que está diseñada para la programación de gráficos acelerados. Esta biblioteca se utiliza únicamente en dispositivos que admiten la funcionalidad nativa de gráficos. Los métodos que se encuentran en el [Graphics espacio de nombres](../../parallel/amp/reference/concurrency-graphics-namespace.md) y están contenidas en el archivo de encabezado \< amp_graphics.h >. Los componentes clave de la biblioteca de gráficos son:  
  
- [Clase de textura](../../parallel/amp/reference/texture-class.md): puede utilizar la clase de textura para crear texturas de memoria o de un archivo. Las texturas son similares a matrices porque contienen datos y se parecen a los contenedores en la biblioteca de plantillas estándar (STL) con respecto a la asignación y construcción de copia. Para obtener más información, consulte [contenedores STL](../../standard-library/stl-containers.md). Los parámetros de plantilla para el `texture` clase son el tipo de elemento y la clasificación. El rango puede ser 1, 2 o 3. El tipo de elemento puede ser uno de los tipos de vector corto que se describen más adelante en este artículo.  
  
- [writeonly_texture_view (clase)](../../parallel/amp/reference/writeonly-texture-view-class.md): proporciona acceso de solo escritura a cualquier textura.  
  
- [Biblioteca de vectores de cortocircuito](http://msdn.microsoft.com/es-es/4c4f5bed-c396-493b-a238-c347563f645f): define un conjunto de tipos de vector corto de longitud 2, 3 y 4 que se basan en `int`, `uint`, `float`, `double`, [norm](../../parallel/amp/reference/norm-class.md), o [unorm](../../parallel/amp/reference/unorm-class.md).  
  
## <a name="includewin8appnamelongtokenwin8appnamelongmdmd-apps"></a>Aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]  
 Al igual que otras bibliotecas de C++, puede usar C++ AMP en su [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplicaciones. Estos artículos describen cómo incluir código de C++ AMP en aplicaciones que se crea mediante C++, C#, Visual Basic o JavaScript:  
  
- [Usar C++ AMP en aplicaciones de la tienda de Windows](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [Tutorial: Crear un componente básico de tiempo de ejecución de Windows en C++ y llamarlo desde JavaScript](http://go.microsoft.com/fwlink/p/LinkId=249077)  
  
- [Mapas de Bing optimizador de recorridos de una aplicación de tienda Windows en JavaScript y C++](http://go.microsoft.com/fwlink/p/LinkId=249078)  
  
- [Cómo utilizar C++ AMP de C# con el tiempo de ejecución de Windows](http://go.microsoft.com/fwlink/p/LinkId=249080)  
  
- [Cómo utilizar C++ AMP de C#](http://go.microsoft.com/fwlink/p/LinkId=249081)  
  
- [Llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP y el visualizador de simultaneidad  
 El visualizador de simultaneidad incluye compatibilidad para analizar el rendimiento de código de C++ AMP. Estos artículos describen estas características:  
  
- [Gráfico de la actividad GPU](../Topic/GPU%20Activity%20Graph.md)  
  
- [Actividad GPU (paginación)](../Topic/GPU%20Activity%20\(Paging\).md)  
  
- [Actividad GPU (este proceso)](../Topic/GPU%20Activity%20\(This%20Process\).md)  
  
- [Actividad GPU (otros procesos)](../Topic/GPU%20Activity%20\(Other%20Processes\).md)  
  
- [Canales (vista de subprocesos)](../Topic/Channels%20\(Threads%20View\).md)  
  
- [Análisis de código de AMP de C++ con el visualizador de simultaneidad](http://go.microsoft.com/fwlink/LinkID=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>Recomendaciones de rendimiento  
 Módulo y división de enteros sin signo tienen el rendimiento significativamente mejor que la división de enteros con signo y el módulo. Se recomienda utilizar enteros sin signo, cuando sea posible.  
  
## <a name="see-also"></a>Vea también  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Sintaxis de expresiones lambda](../../cpp/lambda-expression-syntax.md)   
 [Referencia (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [Programación en paralelo en código nativo](http://go.microsoft.com/fwlink/p/LinkId=238472)
