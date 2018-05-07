---
title: Error de compilador advertencia (nivel 1) C4789 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4789
dev_langs:
- C++
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8b16fada030783f5f9e3aa3d1f9a04e7743a13c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4789"></a>Advertencia del compilador (nivel 1) C4789
se producirá una saturación del búfer 'identificador' con un tamaño de N bytes; se escribirán M bytes empezando en el desplazamiento L  
  
 Advierte de saturación del búfer cuando se usan funciones específicas de tiempo de ejecución de C (CRT), se pasan parámetros y se realizan asignaciones, de forma que el tamaño de los datos se conoce en tiempo de compilación. Esta advertencia se usa en situaciones en las que puede eludirse la detección de discrepancias de tamaño de datos.  
  
 La advertencia aparece cuando los datos, cuya longitud se conoce en tiempo de compilación, se copian y se colocan en un bloque de datos cuyo tamaño se revela —en tiempo de compilación— insuficiente para albergar los datos. La copia debe hacerse mediante la forma intrínseca de una de las siguientes funciones de CRT:  
  
-   [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)  
  
-   [memset](../../c-runtime-library/reference/memset-wmemset.md)  
  
-   [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)  
  
 La advertencia también aparece cuando se produce un error de coincidencia de tipos de datos de parámetro al usar una conversión de tipos y, a continuación, se intenta realizar una asignación de copia de una referencia lvalue.  
  
 Visual C++ puede generar esta advertencia para una ruta de acceso del código que no se ejecuta nunca. La advertencia se puede deshabilitar temporalmente con `#pragma`, como se muestra en este ejemplo:  
  
 `#pragma(push)`  
  
 `#pragma warning ( disable : 4789 )`  
  
 `// unused code that generates compiler warning C4789`  
  
 `#pragma(pop)`  
  
 Esto impide que Visual C++ genera la advertencia para ese bloque de código específico. `#pragma(push)` conserva el estado antes de que `#pragma warning(disable: 4789)` lo cambie. `#pragma(pop)` restaura el estado insertado y quita los efectos de la `#pragma warning(disable:4789)`. Para obtener más información acerca de la directiva de preprocesador de C++ `#pragma`, consulte [advertencia](../../preprocessor/warning.md) y [directivas Pragma y la palabra clave __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C4789.  
  
```  
// C4789.cpp  
// compile with: /Oi /W1 /c  
#include <string.h>  
#include <stdio.h>  
  
int main()   
{  
    char a[20];  
    strcpy(a, "0000000000000000000000000\n");   // C4789  
  
    char buf2[20];  
    memset(buf2, 'a', 21);   // C4789  
  
    char c;  
    wchar_t w = 0;  
    memcpy(&c, &w, sizeof(wchar_t));  
}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente también genera el error C4789.  
  
```  
// C4789b.cpp  
// compile with: /W1 /O2 /c  
// processor: x86  
short G;  
  
void main()  
{  
   int * p = (int *)&G;   
   *p = 3;   // C4789 - writes an int through a pointer to short  
}   
```