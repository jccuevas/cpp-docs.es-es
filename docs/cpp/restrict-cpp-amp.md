---
title: restringir (C++ AMP) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- cpu_CPP
- amp_CPP
dev_langs:
- C++
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abe3bd4f737cfb26a326a1f0d83b731c36e6c7bf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)
El especificador de restricción se puede aplicar a declaraciones de función y lambda. Impone restricciones en el código de la función y en el comportamiento de la función en aplicaciones que utilizan el runtime C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Para obtener información sobre la `restrict` palabra clave que forma parte de la `__declspec` atributos de clase de almacenamiento, consulte [restringir](../cpp/restrict.md).  
  
 La cláusula `restrict` adopta las formas siguientes:  
  
|Cláusula|Descripción|  
|------------|-----------------|  
|`restrict(cpu)`|La función puede usar el lenguaje de C++ completo. Solo otras funciones declaradas mediante funciones restrict(cpu) pueden llamar a la función.|  
|`restrict(amp)`|La función solo puede usar el subconjunto del lenguaje C++ que C++ AMP pueda acelerar.|  
|Secuencia de `restrict(cpu)` y `restrict(amp)`.|La función debe cumplir las limitaciones de `restrict(cpu)` y `restrict(amp)`. La función puede ser objeto de llamadas desde funciones declaradas mediante `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` o `restrict(amp, cpu)`.<br /><br /> La forma `restrict(A) restrict(B)` puede escribirse como `restrict(A,B)`.|  
  
## <a name="remarks"></a>Comentarios  
 La palabra clave `restrict` es una palabra clave contextual. Los especificadores de restricción `cpu` y `amp` no son palabras reservadas. La lista de especificadores no es extensible. Una función que no tiene una cláusula `restrict` es igual que una función con la cláusula `restrict(cpu)`.  
  
 Una función que incluye la cláusula `restrict(amp)` tiene las siguientes limitaciones:  
  
-   La función puede llamar solo a funciones que tengan la cláusula `restrict(amp)`.  
  
-   La función se debe poder insertar.  
  
-   La función solo puede declarar variables `int`, `unsigned int`, `float` y `double`, así como las clases y estructuras que contengan solo estos tipos. `bool` también se permite, pero debe ser un tipo alineado de 4 bytes si se usa en un tipo compuesto.  
  
-   Las funciones lambda no pueden capturar por referencia, y no pueden capturar punteros.  
  
-   Las referencias y los punteros de un solo direccionamiento indirecto se admiten únicamente como variables locales, argumentos de función y tipos de valor devuelto.  
  
-   No se permite lo siguiente:  
  
    -   La recursividad.  
  
    -   Las variables declaradas con el [volátiles](../cpp/volatile-cpp.md) palabra clave.  
  
    -   Funciones virtuales.  
  
    -   Punteros a funciones.  
  
    -   Punteros a funciones miembro.  
  
    -   Punteros en estructuras.  
  
    -   Punteros a punteros.  
  
    -   Instrucciones `goto`.  
  
    -   Instrucciones con etiqueta.  
  
    -   Instrucciones `try`, `catch` o `throw`.  
  
    -   Variables globales.  
  
    -   Variables estáticas. Use [tile_static (palabra clave)](../cpp/tile-static-keyword.md) en su lugar.  
  
    -   Conversiones `dynamic_cast`.  
  
    -   El operador `typeid`.  
  
    -   Declaraciones asm.  
  
    -   Varargs.  
  
 Para obtener una explicación de las limitaciones de la función, vea [restrict(amp) restricciones](http://go.microsoft.com/fwlink/p/?LinkId=251089).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `restrict(amp)`cláusula.  
  
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
  
## <a name="see-also"></a>Vea también  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)