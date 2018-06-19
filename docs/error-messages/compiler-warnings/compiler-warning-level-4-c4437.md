---
title: Compilador advertencia (nivel 4) C4437 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748ba39d9c22a4071307b8df075eab233f3cfbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298332"
---
# <a name="compiler-warning-level-4-c4437"></a>Advertencia del compilador (nivel 4) C4437
dynamic_cast de 'clase1' base virtual a 'clase2' podría producir un error en algunos contextos compilación con/vd2 o definir 'clase2' con #pragma vtordisp(2) en vigor  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 El compilador detectó un `dynamic_cast` operación con las siguientes características.  
  
-   La conversión es de un puntero de clase base a un puntero de la clase derivada.  
  
-   La clase derivada hereda virtualmente la clase base.  
  
-   La clase derivada no tiene un `vtordisp` campo para la base virtual.  
  
-   La conversión no se encuentra en un constructor o destructor de la clase derivada o alguna clase que más se hereda de la clase derivada (en caso contrario, advertencia del compilador se emitirán C4436).  
  
 La advertencia indica que la `dynamic_cast` posible que no funcionen correctamente si se está ejecutando en un objeto construido parcialmente.  Esta situación se produce cuando se llama a la función de inclusión de un constructor o destructor de una clase que hereda de la clase derivada que se menciona en la advertencia.  Si la clase derivada que se menciona en la advertencia nunca es más derivado, o la función de inclusión no se llama durante la construcción de objetos o de destrucción, puede hacer caso omiso de la advertencia.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4437 y muestra el problema de generación de código que surge de la falta `vtordisp` campo.  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
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
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
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
 [Advertencia del compilador (nivel 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)