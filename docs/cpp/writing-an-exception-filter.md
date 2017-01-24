---
title: "Escribir un filtro de excepci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones, filtros"
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Escribir un filtro de excepci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para controlar una excepción puede saltar al nivel del controlador de la excepción o puede continuar la ejecución.  En lugar de utilizar el código de controlador de excepciones para controlar la excepción y pasar por ella, puede usar *filter* para corregir el problema y después, con el valor devuelto – 1, reanudar el flujo normal sin borrar la pila.  
  
> [!NOTE]
>  Algunas excepciones impiden que continúe el flujo.  Si *filter* se evalúa como –1 para una de estas excepciones, el sistema genera una nueva excepción.  Puede determinar si la excepción continuará llamando a [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552).  
  
 Por ejemplo, el código siguiente utiliza una llamada a una función en la expresión *filter*: esta función controla el problema y devuelve – 1 para reanudar el flujo de control normal:  
  
```  
// exceptions_Writing_an_Exception_Filter.cpp  
#include <windows.h>  
int main() {  
   int Eval_Exception( int );  
  
   __try {}  
  
   __except ( Eval_Exception( GetExceptionCode( ))) {  
      ;  
   }  
  
}  
void ResetVars( int ) {}  
int Eval_Exception ( int n_except ) {  
   if ( n_except != STATUS_INTEGER_OVERFLOW &&   
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions  
   return EXCEPTION_CONTINUE_SEARCH;  
  
   // Execute some code to clean up problem  
   ResetVars( 0 );   // initializes data to 0  
   return EXCEPTION_CONTINUE_EXECUTION;  
}  
```  
  
 Es conveniente utilizar una llamada a una función en la expresión *filter* siempre que *filter* necesite realizar alguna tarea compleja.  La evaluación de la expresión hace que se ejecute la función \(en este caso, `Eval_Exception`\).  
  
 Observe el uso de [GetExceptionCode](http://msdn.microsoft.com/library/windows/desktop/ms679356) para determinar la excepción.  Debe llamar a esta función dentro del propio filtro.  `Eval_Exception` no puede llamar a **GetExceptionCode**, pero debe contener el código de la excepción.  
  
 Este controlador pasa el control a otro controlador a menos que la excepción sea un desbordamiento de números enteros o de punto flotante.  En tal caso, el controlador llama a una función \(`ResetVars` es solo un ejemplo, no una función API\) para restablecer algunas variables globales.  *Statement\-block\-2*, que en este ejemplo está vacío, no se puede ejecutar nunca porque `Eval_Exception` nunca devuelve EXCEPTION\_EXECUTE\_HANDLER \(1\).  
  
 El uso de una llamada a una función es una buena técnica de uso general para trabajar con expresiones de filtro complejas.  Otras dos características útiles del lenguaje C son:  
  
-   El operador condicional  
  
-   El operador de coma  
  
 El operador condicional es útil en muchas ocasiones, porque se puede utilizar para comprobar un código de retorno concreto y después devolver uno de dos valores diferentes.  Por ejemplo, el filtro del código siguiente reconoce la excepción solo si la excepción es `STATUS_INTEGER_OVERFLOW`:  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {  
```  
  
 El propósito del operador condicional en este caso es principalmente proporcionar claridad, ya que el código siguiente genera los mismos resultados:  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {  
```  
  
 El operador condicional es más útil en situaciones en las que desee que el filtro se evalúe como – 1, EXCEPTION\_CONTINUE\_EXECUTION.  
  
 El operador de coma permite realizar varias operaciones independientes en una sola expresión.  El efecto es prácticamente el mismo que cuando se ejecutan varias instrucciones y después se devuelve el valor de la última expresión.  Por ejemplo, el código siguiente almacena el código de excepción en una variable y después lo comprueba:  
  
```  
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )  
```  
  
## Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)