---
title: Organización de código fuente (plantillas de C++)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 1933758e47f2fcc0b63f0d16809591b932501854
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611397"
---
# <a name="source-code-organization-c-templates"></a>Organización de código fuente (plantillas de C++)

Al definir una plantilla de clase, debe organizar el código fuente de tal manera que las definiciones de miembro sean visibles para el compilador cuando las necesite.   Tiene la opción de utilizar el *modelo de inclusión* o de*creación de instancias explícita*. En el modelo de inclusión, se incluyen las definiciones de miembro en todos los archivos que usa una plantilla. Este enfoque es más sencillo y proporciona la máxima flexibilidad en cuanto a qué tipos concretos se pueden usar con la plantilla. La desventaja es que pueden aumentar los tiempos de compilación. El impacto puede ser significativo si un proyecto o los archivos incluidos tienen un gran tamaño. Con el enfoque de creación de instancias explícita, la propia plantilla crea instancias de clases concretas o miembros de clase para tipos específicos.  Este enfoque puede acelerar los tiempos de compilación, pero limita el uso a solo las clases que ha habilitado el implementador de plantilla antes de tiempo. En general, se recomienda usar el modelo de inclusión, a menos que los tiempos de compilación se conviertan en un problema.

## <a name="background"></a>Fondo

Las plantillas no son similares a las clases normales en el sentido de que el compilador no genera código de objeto para una plantilla o cualquiera de sus miembros. No se genera nada hasta que se crea una instancia de la plantilla con tipos concretos. Cuando el compilador encuentra una instancia de plantilla como `MyClass<int> mc;` y aún no existe ninguna clase con esa firma, genera una nueva clase. También intenta generar código para las funciones miembro que se usan. Si esas definiciones se encuentran en un archivo que no está incluido, directa o indirectamente, en el archivo .cpp que se está compilando, el compilador no puede verlas.  Desde el punto de vista del compilador, esto no es necesariamente un error porque las funciones pueden definirse en otra unidad de traducción, en cuyo caso el vinculador las encontrará.  Si el vinculador no encuentra ese código, genera un error **externo sin resolver**.

## <a name="the-inclusion-model"></a>El modelo de inclusión

La manera más sencilla y habitual para hacer visible las definiciones de plantilla en una unidad de traducción es poner las definiciones en el propio archivo de encabezado.  Cualquier archivo .cpp que usa la plantilla solo tiene que incluir el encabezado. Este es el enfoque usado en la biblioteca estándar.

```cpp
#ifndef MYARRAY
#define MYARRAY
#include <iostream>

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    // Full definitions:
    MyArray(){}
    void Print()
    {
        for (const auto v : arr)
        {
            std::cout << v << " , ";
        }
    }

    T& operator[](int i)
   {
       return arr[i];
   }
};
#endif
```

Con este enfoque, el compilador tiene acceso a la definición de plantilla completa y puede crear instancias de plantillas y a petición para cualquier tipo. Es sencillo y relativamente fácil de mantener. Sin embargo, el modelo de inclusión tiene un costo en términos de tiempos de compilación.   Este costo puede ser considerable en programas de gran tamaño, especialmente si el encabezado de plantilla propio incluye otros encabezados. Cada archivo .cpp que incluye el encabezado obtendrá su propia copia de las plantillas de función y todas las definiciones. El vinculador suele ser capaz de solucionar los problemas para que no se generen varias definiciones para una función, pero se necesita tiempo para hacer este trabajo. En los programas más pequeños, ese tiempo de compilación adicional probablemente no es significativo.

## <a name="the-explicit-instantiation-model"></a>El modelo de creación de instancias explícita

Si el modelo de inclusión no es viable para el proyecto y sabe con certeza el conjunto de tipos que se usará para crear una instancia de una plantilla, puede separar el código de plantilla en un archivo .h y .cpp, y en el archivo .cpp crear explícitamente instancias de las plantillas. Esto hará que se genere el código objeto que el compilador verá cuando encuentra las creaciones de instancias de usuario.

Cree una instancia explícita mediante el uso de la palabra clave "template" seguida por la firma de la entidad de la que desea crear una instancia. Esto puede ser un tipo o miembro. Si crea una instancia de un tipo explícitamente, se crean instancias de todos los miembros.

```cpp
template MyArray<double, 5>;
```

```cpp
//MyArray.h
#ifndef MYARRAY
#define MYARRAY

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    MyArray();
    void Print();
    T& operator[](int i);
};
#endif

//MyArray.cpp
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for(const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

En el ejemplo anterior, la creación de instancias explícita está en la parte inferior del archivo. cpp. `MyArray` puede utilizarse solo para tipos **double** o `String`.

> [!NOTE]
> En C ++ 11, la palabra clave **export** ha quedado en desuso en el contexto de las definiciones de plantilla. En términos prácticos, esto tiene poco impacto porque la mayoría de los compiladores nunca son compatibles.