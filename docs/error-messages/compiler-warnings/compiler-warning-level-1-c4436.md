---
title: Compilador advertencia (nivel 1) C4436 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1da06a329a9c0bdfcff6877ce69c8e3672619bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4436"></a>Advertencia del compilador (nivel 1) C4436
dynamic_cast de 'clase1' base virtual a 'clase2' en el constructor o destructor podría producir un error con la compilación de objetos construidos parcialmente con/vd2 o definir 'clase2' con #pragma vtordisp(2) en vigor  
  
 El compilador detectó un `dynamic_cast` operación con las siguientes características.  
  
-   La conversión es de un puntero de clase base a un puntero de la clase derivada.  
  
-   La clase derivada hereda virtualmente la clase base.  
  
-   La clase derivada no tiene un `vtordisp` campo para la base virtual.  
  
-   La conversión se encuentra en un constructor o destructor de la clase derivada o alguna clase que más se hereda de la clase derivada.  
  
 La advertencia indica la `dynamic_cast` posible que no funcionen correctamente, si se está ejecutando en un objeto construido parcialmente.  Esto sucede si el constructor o destructor derivado está en funcionamiento en un objeto secundario de algún objeto más derivado.  Si la clase derivada con el nombre de la advertencia nunca es más derivado, la advertencia puede omitirse.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4436 y muestra el problema de generación de código que surge de la falta `vtordisp` campo.  
  
```cpp  
// C4436.cpp  
// To see the warning and runtime assert, compile with: /W1  
// To eliminate the warning and assert, compile with: /W1 /vd2  
//       or compile with: /W1 /DFIX  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4436  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [dynamic_cast (operador)](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Advertencia del compilador (nivel 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)