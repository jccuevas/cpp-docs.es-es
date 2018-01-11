---
title: "Cómo: exponer un contenedor STL/CLR desde un ensamblado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84505edf0877a5ae20d28906dde7f4c709574034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Cómo: Exponer un contenedor de STL/CLR desde un ensamblado
Contenedores STL/CLR como `list` y `map` se implementan como clases ref de plantilla. Dado que se crean instancias de las plantillas de C++ en tiempo de compilación, dos clases de plantilla que tienen exactamente la misma firma, pero están en distintos ensamblados son realmente diferentes tipos. Esto significa que no se puede usar las clases de plantilla en los límites del ensamblado.  
  
 Para que compartir entre ensamblados sea posible, los contenedores STL/CLR implementan la interfaz genérica <xref:System.Collections.Generic.ICollection%601>. Mediante el uso de esta interfaz genérica, todos los idiomas que admiten genéricos, incluyendo C++, C# y Visual Basic, pueden tener acceso a contenedores STL/CLR.  
  
 Este tema muestra cómo mostrar los elementos de varios contenedores STL/CLR que se escribe en un ensamblado de C++ denominado `StlClrClassLibrary`. Se muestran dos ensamblados tengan acceso a `StlClrClassLibrary`. El primer ensamblado está escrito en C++ y la segunda en C#.  
  
 Si ambos ensamblados están escritos en C++, puede tener acceso a la interfaz genérica de un contenedor mediante su `generic_container` typedef. Por ejemplo, si tiene un contenedor de tipo `cliext::vector<int>`, entonces su interfaz genérica es: `cliext::vector<int>::generic_container`. De forma similar, puede obtener un iterador a través de la interfaz genérica con el `generic_iterator` typedef, como en: `cliext::vector<int>::generic_iterator`.  
  
 Puesto que estas definiciones de tipos se declaran en los archivos de encabezado de C++, ensamblados escritos en otros lenguajes no pueden usarlos. Por lo tanto, para tener acceso a la interfaz genérica para `cliext::vector<int>` en C# o cualquier otro lenguaje. NET, use `System.Collections.Generic.ICollection<int>`. Para recorrer en iteración esta colección, use un `foreach` bucle.  
  
 La tabla siguiente muestra la interfaz genérica que implementa cada contenedor STL/CLR:  
  
|Contenedor STL/CLR|Interfaz genérica|  
|------------------------|-----------------------|  
|deque < T\>|ICollection < T\>|  
|hash_map < K, V >|IDictionary < K, V >|  
|hash_multimap < K, V >|IDictionary < K, V >|  
|hash_multiset < T\>|ICollection < T\>|  
|hash_set < T\>|ICollection < T\>|  
|lista < T\>|ICollection < T\>|  
|asignar < K, V >|IDictionary < K, V >|  
|multimap < K, V >|IDictionary < K, V >|  
|MULTISET < T\>|ICollection < T\>|  
|Establezca < T\>|ICollection < T\>|  
|vector < T\>|ICollection < T\>|  
  
> [!NOTE]
>  Dado que la `queue`, `priority_queue`, y `stack` contenedores no admiten iteradores, implementar interfaces genéricas y no pueden ser el acceso entre ensamblados.  
  
## <a name="example-1"></a>Ejemplo 1  
  
### <a name="description"></a>Descripción  
 En este ejemplo, se declara una clase de C++ que contiene los datos de miembros privados de STL/CLR. A continuación, se declaran los métodos públicos para conceder acceso a las colecciones privadas de la clase. Hacemos lo de dos maneras diferentes, uno para los clientes C++ y otro para otros clientes. NET.  
  
### <a name="code"></a>Código  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="example-2"></a>Ejemplo 2  
  
### <a name="description"></a>Descripción  
 En este ejemplo, se implementa la clase declarada en el ejemplo 1. En orden para los clientes que usen esta biblioteca de clases, se utiliza la herramienta manifiesto **mt.exe** para incrustar el archivo de manifiesto en el archivo DLL. Para obtener más información, vea los comentarios de código.  
  
 Para obtener más información sobre la herramienta manifiesto y ensamblados en paralelo, vea [C/C++ de compilar aplicaciones aisladas y ensamblados en paralelo](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
### <a name="code"></a>Código  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example-3"></a>Ejemplo 3  
  
### <a name="description"></a>Descripción  
 En este ejemplo, crearemos a un cliente de C++ que utiliza la biblioteca de clases creada en los ejemplos 1 y 2. Este cliente utiliza el `generic_container` definiciones de tipo de los contenedores STL/CLR para iterar sobre los contenedores y mostrar su contenido.  
  
### <a name="code"></a>Código  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="output"></a>Salida  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## <a name="example-4"></a>Ejemplo 4  
  
### <a name="description"></a>Descripción  
 En este ejemplo, se crea a un cliente de C# que utiliza la biblioteca de clases creada en los ejemplos 1 y 2. Este cliente utiliza el <xref:System.Collections.Generic.ICollection%601> métodos de los contenedores STL/CLR para iterar sobre los contenedores y mostrar su contenido.  
  
### <a name="code"></a>Código  
  
```  
// CsConsoleApp.cs  
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll  
  
using System;  
using System.Collections.Generic;  
using StlClrClassLibrary;  
using cliext;  
  
namespace CsConsoleApp  
{  
    class Program  
    {  
        static int Main(string[] args)  
        {  
            StlClrClass theClass = new StlClrClass();  
  
            Console.WriteLine("cliext::deque contents:");  
            ICollection<char> iCollChar = theClass.GetDequeCs();  
            foreach (char c in iCollChar)  
            {  
                Console.WriteLine(c);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::list contents:");  
            ICollection<float> iCollFloat = theClass.GetListCs();  
            foreach (float f in iCollFloat)  
            {  
                Console.WriteLine(f);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::map contents:");  
            IDictionary<int, string> iDict = theClass.GetMapCs();  
            foreach (KeyValuePair<int, string> kvp in iDict)  
            {  
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::set contents:");  
            ICollection<double> iCollDouble = theClass.GetSetCs();  
            foreach (double d in iCollDouble)  
            {  
                Console.WriteLine(d);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::vector contents:");  
            ICollection<int> iCollInt = theClass.GetVectorCs();  
            foreach (int i in iCollInt)  
            {  
                Console.WriteLine(i);  
            }  
            Console.WriteLine();  
  
            return 0;  
        }  
    }  
}  
```  
  
### <a name="output"></a>Salida  
  
```  
cliext::deque contents:  
a  
b  
  
cliext::list contents:  
3.14159  
2.71828  
  
cliext::map contents:  
0 Hello  
1 World  
  
cliext::set contents:  
2.71828  
3.14159  
  
cliext::vector contents:  
10  
20  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)