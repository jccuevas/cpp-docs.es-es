---
title: "Controlador de seguimiento de un valor al que se le ha aplicado la conversi&#243;n boxing | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "tipos de valor con la conversión boxing aplicada, identificador de seguimiento"
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controlador de seguimiento de un valor al que se le ha aplicado la conversi&#243;n boxing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso de un controlador de seguimiento que haga referencia a un tipo de valor ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 La conversión boxing es una peculiaridad del sistema de tipos unificado de CLR.  Los tipos de valores contienen directamente su estado, mientras que los tipos de referencia son un par implícito: la entidad con nombre es un controlador de un objeto sin nombre asignado al montón administrado.  Cualquier inicialización o asignación del tipo de valor a un `Object`, por ejemplo, requiere que el tipo de valor se coloque dentro del montón de CLR, ahí es donde surge la imagen de la conversión boxing, asignando primero la memoria asociada, copiando el estado del tipo de valor y devolviendo la dirección de este híbrido de valor\/referencia anónimo.  Así, cuando se escribe en C\#  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 hay muchas más cosas de lo que a primera vista parece debido a la sencillez del código.  El diseño de C\# oculta la complejidad no sólo de las operaciones que se están desarrollando a cubierto, sino también de la abstracción de la conversión boxing en sí misma.  Por otra parte, Extensiones administradas para C\+\+, consciente de que esto llevaría a un falso significado de la eficacia, lo ponía de manifiesto ante el usuario al solicitarle una instrucción explícita:  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 La conversión boxing es implícita en [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)]:  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 La palabra clave `__box` proporciona un servicio de vital importancia en Extensiones administradas que, por diseño, no está presente en lenguajes como C\# y [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)]: ofrece un vocabulario y un controlador de seguimiento para manipular directamente una instancia de conversión boxing en el montón administrado.  Por ejemplo, considere el pequeño programa siguiente:  
  
```  
int main() {  
   double result = 3.14159;  
   __box double * br = __box( result );  
  
   result = 2.7;   
   *br = 2.17;     
   Object * o = br;  
  
   Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
   Console::WriteLine( S"result :: {0}", __box(result) ) ;  
   Console::WriteLine( S"result :: {0}", br );  
}  
```  
  
 El código subyacente generado para las tres invocaciones de `WriteLine` muestra los distintos costos de acceso al valor de un tipo de valor de conversión boxing \(agradecemos a Yves Dolce que haya señalado estas diferencias\), en el que las líneas indicadas muestran la sobrecarga asociada a cada invocación.  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
call       void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", __box(result) ) ;  
Ldstr    " result :: {0}"  
ldloc.0  
box    [mscorlib]System.Double // box overhead  
call    void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", br );  
ldstr    "result :: {0}"  
ldloc.0  
call     void [mscorlib]System.Console::WriteLine(string, object)  
```  
  
 Al pasar el tipo de valor de conversión boxing directamente a `Console::WriteLine`, se eliminan la conversión boxing y la necesidad de invocar `ToString()`. \(Por supuesto, se puede utilizar la conversión boxing anterior para inicializar `br`, pero no ganamos nada a menos que lo que deseemos realmente sea hacer trabajar a `br`\).  
  
 En la nueva sintaxis, la compatibilidad para los tipos de valor de conversión boxing es mucho más elegante y está integrada dentro del sistema de tipos, a la vez que conserva su poder.  Por ejemplo, ésta es la traducción del pequeño programa anterior:  
  
```  
int main()  
{  
   double result = 3.14159;  
   double^ br = result;  
   result = 2.7;  
   *br = 2.17;  
   Object^ o = br;  
   Console::WriteLine( "result :: {0}", result.ToString() );  
   Console::WriteLine( "result :: {0}", result );  
   Console::WriteLine( "result :: {0}", br );  
}  
```  
  
## Vea también  
 [Tipos de valor y su comportamiento \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)