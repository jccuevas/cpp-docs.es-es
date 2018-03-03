---
title: "Un controlador de seguimiento en un valor de conversión boxing | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: baae8c5317f1e5c9c5acf5bef26a4b79de281a3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Controlador de seguimiento de un valor al que se le ha aplicado la conversión boxing
El uso de un controlador de seguimiento a un tipo de valor de referencia ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 La conversión boxing es una característica del sistema de tipos CLR unificado. Tipos de valor contienen directamente su estado, mientras que los tipos de referencia son un par implícito: la entidad con nombre es un identificador de un objeto sin nombre asignado en el montón administrado. Cualquier inicialización o asignación de un valor de tipo a un `Object`, por ejemplo, requiere que el tipo de valor se coloquen en el montón CLR: Esto es donde se produce la imagen de la conversión boxing - primero al asignar la memoria asociada, a continuación, mediante la copia de estado del tipo de valor y, a continuación, devolver la dirección de este híbrido de valor/referencia anónimo. Por lo tanto, cuando se escribe en C#  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 hay mucho más cosas que estará aparente mediante la sencillez del código. El diseño de C# oculta la complejidad no sólo de las operaciones que tienen lugar en segundo plano, sino también de la abstracción de la conversión boxing a sí mismo. Extensiones administradas para C++, por otro lado, que se trate que Esto conduciría a una falsa sensación de eficacia, lo coloca en la cara del usuario solicitando una instrucción explícita:  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 La conversión boxing es implícita en Visual C++:  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 El `__box` (palabra clave) proporciona un servicio vital en extensiones administradas, uno que no están presentes en el diseño de lenguajes como C# y Visual Basic: ofrece un vocabulario y el seguimiento de un controlador para la manipulación directa de una instancia de conversión boxing en el montón administrado. Por ejemplo, considere el pequeño programa siguiente:  
  
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
  
 El código subyacente generado para las tres invocaciones de `WriteLine` mostrar los distintos costos de acceso al valor de un valor de conversión boxing escriba (agradecemos a Yves Dolce para aclarar estas diferencias), donde las líneas indicadas muestran la sobrecarga asociada a cada uno invocación.  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
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
  
 Pasar el tipo de valor de conversión boxing directamente al `Console::WriteLine` elimina la conversión boxing y la necesidad de invocar `ToString()`. (Por supuesto, hay la conversión boxing anterior para inicializar `br`, por lo que no obtenemos nada a menos que realmente colocamos `br` para que funcione.  
  
 En la nueva sintaxis, la compatibilidad con tipos de valor con conversión boxing es considerablemente más elegante y está integrada en el sistema de tipos conservando su funcionalidad. Por ejemplo, ésta es la traducción del pequeño programa anterior:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Tipos de valor y sus comportamientos (C++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)