---
title: "C&#243;mo: Definir y usar enumeraciones en C++/CLI | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enum (clase), especificar tipos subyacentes"
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Definir y usar enumeraciones en C++/CLI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema describe las enumeraciones en C\+\+\/CLI.  
  
## Especificar el tipo subyacente de una enumeración  
 De forma predeterminada, el tipo subyacente de una enumeración es `int`.  Sin embargo, puede especificar el tipo que se firmarán o formularios sin signo de `int`, de `short`, de `long`, de `__int32`, o de `__int64`.  También puede utilizar `char`.  
  
```  
// mcppv2_enum_3.cpp  
// compile with: /clr  
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};  
  
int main() {  
   // fully qualified names, enumerator not injected into scope  
   day_char d = day_char::sun, e = day_char::mon;  
   System::Console::WriteLine(d);  
   char f = (char)d;  
   System::Console::WriteLine(f);  
   f = (char)e;  
   System::Console::WriteLine(f);  
   e = day_char::tue;  
   f = (char)e;  
   System::Console::WriteLine(f);  
}  
```  
  
 **Resultados**  
  
  **sol**  
**0**  
**1**  
**2**   
## Cómo convertir entre enumeraciones administradas y estándar  
 No hay ninguna conversión estándar entre una enumeración y un tipo entero; se requiere una conversión.  
  
```  
// mcppv2_enum_4.cpp  
// compile with: /clr  
enum class day {sun, mon, tue, wed, thu, fri, sat};  
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum  
  
int main() {  
   day a = day::sun;  
   day2 = sun;  
   if ((int)a == day2)  
   // or...  
   // if (a == (day)day2)  
      System::Console::WriteLine("a and day2 are the same");  
   else  
      System::Console::WriteLine("a and day2 are not the same");  
}  
```  
  
 **Resultados**  
  
  **en y day2 son iguales**   
## Operadores y enumeraciones  
 Los operadores válidos en enumeraciones en C\+\+\/CLI:  
  
|operador ??|  
|-----------------|  
|\=\= \!\= \< \> \<\= \>\=|  
|\+ \-|  
|&#124; ^ & ~|  
|\+\+ \-\-|  
|sizeof|  
  
 Operadores &#124; ^ & ~ \+\+ \-\- solo se definen para las enumeraciones con tipos subyacentes enteros, sin incluir bool.  Ambos operandos deben ser del tipo de enumeración.  
  
 El compilador realiza comprobación no estáticos o dinámicos del resultado de una operación de enumeración; una operación puede producir un valor no en el intervalo de los enumeradores válidos de los enum.  
  
> [!NOTE]
>  C\+\+11 escribe código no administrado de los tipos de clase de enumeración en que son significativamente diferente de clases administradas de enumeración en C\+\+\/CLI.  En particular, el tipo de clase de enumeración C\+\+11 no admite los mismos operadores que el tipo de clase administrado enum de C\+\+\/CLI, y el código fuente de C\+\+\/CLI debe proporcionar un especificador de accesibilidad en declaraciones de clase administradas de enumeración para distinguirlas de declaraciones de clase no enum \(C\+\+11\).  Para obtener más información sobre las clases de enumeración en C\+\+\/CLI, C\+\+\/CX, y C\+\+11, vea [enum class](../windows/enum-class-cpp-component-extensions.md).  
  
```  
// mcppv2_enum_5.cpp  
// compile with: /clr  
private enum class E { a, b } e, mask;  
int main() {  
   if ( e & mask )   // C2451 no E->bool conversion  
      ;  
  
   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)  
      ;  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```  
  
```  
// mcppv2_enum_6.cpp  
// compile with: /clr  
private enum class day : int {sun, mon};  
enum : bool {sun = true, mon = false} day2;  
  
int main() {  
   day a = day::sun, b = day::mon;  
   day2 = sun;  
  
   System::Console::WriteLine(sizeof(a));  
   System::Console::WriteLine(sizeof(day2));  
   a++;  
   System::Console::WriteLine(a == b);  
}  
```  
  
 **Resultados**  
  
  **4**  
**1**  
**True**   
## Vea también  
 [enum class](../windows/enum-class-cpp-component-extensions.md)