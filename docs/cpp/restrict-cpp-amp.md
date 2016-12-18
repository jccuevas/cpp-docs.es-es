---
title: "restrict (C++ AMP) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "cpu_CPP"
  - "amp_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "restrict (cláusula) (C++ AMP)"
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# restrict (C++ AMP)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El especificador de restricción se puede aplicar a declaraciones de función y lambda.  Impone restricciones en el código de la función y en el comportamiento de la función en aplicaciones que utilizan el runtime C\+\+ Accelerated Massive Parallelism \(C\+\+ AMP\).  
  
> [!NOTE]
>  Para obtener información sobre la palabra clave `restrict` que forma parte de los atributos de la clase de almacenamiento `__declspec`, vea [restrict](../cpp/restrict.md).  
  
 La cláusula `restrict` adopta las formas siguientes:  
  
|Cláusula|Descripción|  
|--------------|-----------------|  
|`restrict(cpu)`|La función puede usar el lenguaje de C\+\+ completo.  Solo otras funciones declaradas mediante funciones restrict\(cpu\) pueden llamar a la función.|  
|`restrict(amp)`|La función solo puede usar el subconjunto del lenguaje C\+\+ que C\+\+ AMP pueda acelerar.|  
|Secuencia de `restrict(cpu)` y `restrict(amp)`.|La función debe cumplir las limitaciones de `restrict(cpu)` y `restrict(amp)`.  La función puede ser objeto de llamadas desde funciones declaradas mediante `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` o `restrict(amp, cpu)`.<br /><br /> La forma `restrict(A) restrict(B)` puede escribirse como `restrict(A,B)`.|  
  
## Comentarios  
 La palabra clave `restrict` es una palabra clave contextual.  Los especificadores de restricción `cpu` y `amp` no son palabras reservadas.  La lista de especificadores no es extensible.  Una función que no tiene una cláusula `restrict` es igual que una función con la cláusula `restrict(cpu)`.  
  
 Una función que incluye la cláusula `restrict(amp)` tiene las siguientes limitaciones:  
  
-   La función puede llamar solo a funciones que tengan la cláusula `restrict(amp)`.  
  
-   La función se debe poder insertar.  
  
-   La función solo puede declarar variables `int`, `unsigned int`, `float` y `double`, así como las clases y estructuras que contengan solo estos tipos.  `bool` también se permite, pero debe ser un tipo alineado de 4 bytes si se usa en un tipo compuesto.  
  
-   Las funciones lambda no pueden capturar por referencia, y no pueden capturar punteros.  
  
-   Las referencias y los punteros de un solo direccionamiento indirecto se admiten únicamente como variables locales, argumentos de función y tipos de valor devuelto.  
  
-   No se permite lo siguiente:  
  
    -   La recursividad.  
  
    -   Variables declaradas con la palabra clave [volatile](../cpp/volatile-cpp.md).  
  
    -   Funciones virtuales.  
  
    -   Punteros a funciones.  
  
    -   Punteros a funciones miembro.  
  
    -   Punteros en estructuras.  
  
    -   Punteros a punteros.  
  
    -   Instrucciones `goto`.  
  
    -   Instrucciones con etiqueta.  
  
    -   Instrucciones `try`, `catch` o `throw`.  
  
    -   Variables globales.  
  
    -   Variables estáticas.  Utilice [tile\_static \(Palabra clave\)](../cpp/tile-static-keyword.md) en su lugar.  
  
    -   Conversiones `dynamic_cast`.  
  
    -   El operador `typeid`.  
  
    -   Declaraciones asm.  
  
    -   Varargs.  
  
 Para obtener una descripción de las limitaciones de función, vea las [restricciones restrict\(amp\)](http://go.microsoft.com/fwlink/p/?LinkId=251089).  
  
## Ejemplo  
 En el ejemplo siguiente, se muestra cómo usar la cláusula `restrict(amp)`.  
  
```  
  
void functionAmp() restrict(amp) {}   
void functionNonAmp() {}   
  
void callFunctions() restrict(amp)   
{   
    // int is allowed.  
    int x;  
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.  
    // long long int y;   
  
    // Calling an amp-restricted function is allowed.  
    functionAmp();   
  
    // Calling a non-amp-restricted function is not allowed.  
    // functionNonAmp();   
  
}  
```  
  
## Vea también  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)