---
title: "C&#243;mo: Exponer un contenedor de STL/CLR desde un ensamblado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores STL/CLR [STL/CLR]"
  - "STL/CLR, problemas entre ensamblados"
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Exponer un contenedor de STL/CLR desde un ensamblado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los contenedores de STL\/CLR como `list` y `map` se implementan como clases de referencia de la plantilla.  Dado que las plantillas de C\+\+ se crean instancias en tiempo de compilación, dos clases de plantilla que tienen exactamente la misma firma pero están en distintos ensamblados son realmente tipos diferentes.  Esto significa que las clases de plantilla no se pueden utilizar en los límites del ensamblado.  
  
 Para crear compartir de cruce\- ensamblado posible, implemente de contenedores de STL\/CLR la interfaz genérica <xref:System.Collections.Generic.ICollection%601>.  Con esta interfaz genérica, todos los lenguajes que genéricos compatible con, como C\+\+, C\#, y Visual Basic, pueden tener acceso a los contenedores de STL\/CLR.  
  
 En este tema se muestra cómo mostrar los elementos de varios contenedores de STL\/CLR escritos en c\+\+. `StlClrClassLibrary`denominado ensamblado.  Se muestran dos ensamblados para tener acceso a `StlClrClassLibrary`.  Escriba el primer ensamblado en C\+\+, y el segundo en C\#.  
  
 Si escriben ambos ensamblados en C\+\+, puede tener acceso a la interfaz genérica de un contenedor mediante la definición de `generic_container` .  Por ejemplo, si tiene un contenedor de `cliext::vector<int>`tipo, su interfaz genérica es: `cliext::vector<int>::generic_container`.  De igual forma, puede obtener un iterador sobre la interfaz genérica utilizando typedef de `generic_iterator` , como en: `cliext::vector<int>::generic_iterator`.  
  
 Puesto que estos typedefs se declaran en los archivos de encabezado de C\+\+, ensamblados escritos en otros lenguajes no pueden utilizarlos.  Por consiguiente, tener acceso a la interfaz genérica para `cliext::vector<int>` en C\# o cualquier otro lenguaje.NET, utilice `System.Collections.Generic.ICollection<int>`.  Para iterar sobre esta colección, utilice un bucle de `foreach` .  
  
 La tabla siguiente muestra la interfaz genérica que cada contenedor de STL\/CLR implementa:  
  
|Contenedor de STL\/CLR|Interfaz genérica|  
|----------------------------|-----------------------|  
|dequeT\<\>|ICollectionT\<\>|  
|hash\_mapK\<, V\>|IDictionaryK\<, V\>|  
|hash\_multimapK\<, V\>|IDictionaryK\<, V\>|  
|hash\_multisetT\<\>|ICollectionT\<\>|  
|hash\_setT\<\>|ICollectionT\<\>|  
|listT\<\>|ICollectionT\<\>|  
|mapK\<, V\>|IDictionaryK\<, V\>|  
|multimapK\<, V\>|IDictionaryK\<, V\>|  
|multisetT\<\>|ICollectionT\<\>|  
|adoquín\<\>|ICollectionT\<\>|  
|vectorT\<\>|ICollectionT\<\>|  
  
> [!NOTE]
>  Dado que `queue`, `priority_queue`, y los contenedores de `stack` no admiten iteradores, no implementan interfaces genéricas y no pueden ser cruce\- ensamblado acceso.  
  
## Ejemplo 1  
  
### Descripción  
 En este ejemplo, declaramos la clase en cuestión. que contiene datos privados del miembro de STL\/CLR.  A continuación declaramos métodos públicos para conceder acceso a colecciones privados de la clase.  La hace de dos maneras diferentes, una para los clientes de C\+\+ y otra para otros clientes.NET.  
  
### Código  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## Ejemplo 2  
  
### Descripción  
 En este ejemplo, implementamos la clase declarada en el ejemplo 1.  Para que los clientes utilicen la biblioteca de clases, se usa la herramienta manifiesto **mt.exe** para incrustar el archivo de manifiesto en un archivo DLL.  Para obtener información detallada, vea los comentarios del código.  
  
 Para obtener más información sobre la herramienta y los ensamblados en paralelo de manifiesto, vea [Compilar aplicaciones aisladas y ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
### Código  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## Ejemplo 3  
  
### Descripción  
 En este ejemplo, creamos al cliente en cuestión. que usa la biblioteca de clases creada en los ejemplos 1 y 2.  Este cliente utiliza tipos de `generic_container` de contenedores de STL\/CLR para iterar sobre los contenedores y mostrar su contenido.  
  
### Código  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### Resultados  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## Ejemplo 4  
  
### Descripción  
 En este ejemplo, creamos un cliente de C\# que usa la biblioteca de clases creada en los ejemplos 1 y 2.  Este cliente utiliza los métodos de <xref:System.Collections.Generic.ICollection%601> de contenedores de STL\/CLR para iterar sobre los contenedores y mostrar su contenido.  
  
### Código  
  
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
  
### Resultados  
  
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
  
## Vea también  
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)