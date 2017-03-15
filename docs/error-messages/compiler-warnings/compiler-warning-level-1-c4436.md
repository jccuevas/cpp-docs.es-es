---
title: "Advertencia del compilador (nivel 1) C4436 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# Advertencia del compilador (nivel 1) C4436
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dynamic\_cast de base virtual “clase1” a “clase2” en constructor o destructor podría producir un error con compilación parcial\- construida de objeto con \/vd2 o definir “clase2” con el vtordisp \#pragma \(2\) en efecto  
  
 El compilador ha encontrado una operación de `dynamic_cast` con las características siguientes.  
  
-   La conversión es de un puntero de clase base a un puntero de clase derivada.  
  
-   La clase derivada hereda la clase base.  
  
-   La clase derivada no tiene un campo de `vtordisp` para base virtual.  
  
-   La conversión se encuentra en un constructor o destructor de la clase derivada, o alguna clase que hereda más fuera de la clase derivada.  
  
 La advertencia indica que `dynamic_cast` no realice correctamente, si está trabajando en un objeto parcial\- construido.  Esto sucede si el constructor derivado\/destructor está trabajando en un sub\- objeto de algún otro objeto derivado.  Si la clase derivada denominada en la advertencia nunca es derivada adicional, la advertencia se puede omitir.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4436 y muestra el problema de compilación de código que surge de campo que falta de `vtordisp` .  
  
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
  
## Vea también  
 [dynamic\_cast \(Operador\)](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Advertencia del compilador \(nivel 4\) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)