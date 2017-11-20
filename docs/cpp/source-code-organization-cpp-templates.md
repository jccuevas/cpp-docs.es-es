---
title: "Origen de la organización del código (plantillas de C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
caps.latest.revision: "5"
manager: ghogen
ms.openlocfilehash: 1b3b17c17bad3834774f747548dda6710e178cb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="source-code-organization-c-templates"></a>Organización de código de origen (plantillas de C++)

Al definir una plantilla de clase, debe organizar el código fuente de tal manera que las definiciones de miembro están visibles para el compilador cuando necesita.   Tiene la opción de usar la *modelo de inclusión* o *creación de instancias explícita* modelo. En el modelo de inclusión, se incluyen las definiciones de miembro de cada archivo que usa una plantilla. Este enfoque es más sencillo y ofrece la máxima flexibilidad en cuanto a qué tipos concretos pueden usarse con la plantilla. La desventaja es que puede aumentar los tiempos de compilación. El impacto puede ser considerable si un proyecto o los archivos incluidos por sí mismos son grandes. Con el enfoque de creación de instancias explícita, la plantilla crea instancias de clases concretas o miembros de clase para tipos específicos.  Este enfoque puede acelerar tiempos de compilación, pero limita el uso de sólo a las clases que ha habilitado el implementador de la plantilla antes de tiempo. En general, se recomienda utilizar el modelo de inclusión a menos que los tiempos de compilación se conviertan en un problema.  
  
## <a name="background"></a>Fondo

 Las plantillas no son las clases normales en el sentido de que el compilador no genera código de objeto de una plantilla o cualquiera de sus miembros. No hay nada que generar hasta que se crea una instancia de la plantilla con tipos concretos. Cuando el compilador encuentra una creación de instancias de plantilla como `MyClass<int> mc;` y aún no existe ninguna clase con esa firma, genera una nueva clase. También intenta generar código para las funciones miembro que se utilizan. Si esas definiciones están en un archivo que no es #included, directa o indirectamente, en el archivo .cpp que se está compilando, el compilador no puede verlo.  Desde el punto de vista del compilador, esto no es necesariamente un error porque las funciones se pueden definir en otra unidad de traducción, en el que caso el vinculador encuentren fácilmente.  Si el vinculador no encuentra ese código, genera un **externo sin resolver** error.  

## <a name="the-inclusion-model"></a>El modelo de inclusión

 La manera más sencilla y más común para hacer visible a lo largo de una unidad de traducción, las definiciones de plantilla es poner las definiciones en el propio archivo de encabezado.  Cualquier archivo .cpp que usa la plantilla simplemente tiene que #include el encabezado. Este es el enfoque usado en la biblioteca estándar.  
  
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
  
 Con este enfoque, el compilador tiene acceso a la definición de plantilla completa y puede crear instancias de plantillas a petición para cualquier tipo. Es relativamente fácil de mantener y sencillo. Sin embargo, el modelo de inclusión tiene un costo en términos de tiempos de compilación.   Este costo puede ser considerable en programas de gran tamaño, especialmente si el encabezado de plantilla propiamente dicho #includes otros encabezados. Archivo cada .cpp que #includes el encabezado obtendrá su propia copia de las plantillas de función y todas las definiciones. El vinculador suele ser capaz de arreglar las cosas para que no terminará con varias definiciones para una función, pero se necesita tiempo para realizar este trabajo. En programas más pequeños que el tiempo de compilación adicionales probablemente no es significativo.  
  
## <a name="the-explicit-instantiation-model"></a>El modelo de creación de instancias explícita

 Si el modelo de inclusión no es viable para el proyecto y se sabe con certeza el conjunto de tipos que se utilizará para crear una instancia de una plantilla, puede separar el código de plantilla en un archivo .h y .cpp y en el archivo .cpp crear explícitamente instancias de las plantillas. Esto hará que se genere el código objeto que el compilador verán cuando encuentra instancias de usuario.  
  
 Crear una instancia explícita mediante la palabra clave template seguida por la firma de la entidad que desea crear una instancia. Puede tratarse de un tipo o un miembro. Si crea una instancia de un tipo de forma explícita, se crean instancias de todos los miembros.  
  
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
#include "stdafx.h"  
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
  
 En el ejemplo anterior, la creación de instancias explícita se encuentran en la parte inferior del archivo .cpp. A `MyArray` puede utilizarse solo para **doble** o **cadena** tipos.  
  
> [!NOTE]
>  En C ++ 11 la **exportar** palabra clave ha quedado obsoleta en el contexto de las definiciones de plantilla. En la práctica, esto tiene poco impacto porque la mayoría de los compiladores nunca admite.
