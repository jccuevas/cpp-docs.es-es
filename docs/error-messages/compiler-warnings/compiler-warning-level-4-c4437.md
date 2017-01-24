---
title: "Advertencia del compilador (nivel 4) C4437 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4437
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dynamic\_cast de base virtual “clase1” a “clase2” podría producir un error de compilación de algunos contextos con \/vd2 o definir “clase2” con el vtordisp \#pragma \(2\) en efecto  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El compilador ha encontrado una operación de `dynamic_cast` con las características siguientes.  
  
-   La conversión es de un puntero de clase base a un puntero de clase derivada.  
  
-   La clase derivada hereda la clase base.  
  
-   La clase derivada no tiene un campo de `vtordisp` para base virtual.  
  
-   La conversión no se encuentra en un constructor o destructor de la clase derivada, o alguna clase que hereda más fuera de la clase derivada \(si no, la advertencia del compilador C4436 se emitirá\).  
  
 La advertencia indica que `dynamic_cast` no realice correctamente si está trabajando en un objeto parcial\- construido.  Esta situación se produce cuando la función envolvente se denomina de un constructor o destructor de una clase que herede la clase derivada denominado en la advertencia.  Si la clase derivada denominado en la advertencia nunca es derivada adicional, o la función envolvente no se llama durante la construcción o destrucción de objetos, la advertencia se puede omitir.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4437 y muestra el problema de compilación de código que surge de campo que falta de `vtordisp` .  
  
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
  
## Vea también  
 [dynamic\_cast \(Operador\)](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Advertencia del compilador \(nivel 1\) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)