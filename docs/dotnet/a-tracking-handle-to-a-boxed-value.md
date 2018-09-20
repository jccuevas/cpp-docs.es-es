---
title: Un controlador de seguimiento en un valor con conversión boxing | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7e26efae93b509700c3bb0c992d9f397559e99f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380738"
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Controlador de seguimiento de un valor al que se le ha aplicado la conversión boxing

El uso de un controlador de seguimiento a un tipo de valor de referencia ha cambiado de extensiones administradas para C++ a Visual C++.

Conversión boxing es una peculiaridad del sistema de tipos unificado de CLR. Tipos de valor contienen directamente su estado, mientras que los tipos de referencia son un par implícito: la entidad con nombre es un identificador para un objeto sin nombre asignado en el montón administrado. Cualquier inicialización o asignación de un valor de tipo a un `Object`, por ejemplo, requiere que el tipo de valor se coloque dentro del montón CLR: es donde se produce la imagen de la conversión boxing - primero mediante la asignación de la memoria asociada, copiando el estado del tipo de valor y, a continuación, devolver la dirección de este híbrido de valor o referencia anónimo. Por lo tanto, cuando se escribe en C#

```cpp
object o = 1024; // C# implicit boxing
```

No hay mucho más cosas que queda evidente por la sencillez del código. El diseño de C# oculta la complejidad no sólo de las operaciones que están teniendo lugar en segundo plano, sino también de la abstracción de la conversión boxing a sí mismo. Extensiones administradas para C++, por otro lado, que se trate esto daría lugar a una falsa sensación de eficacia, lo coloca en frente al usuario solicitando una instrucción explícita:

```cpp
Object *o = __box( 1024 ); // Managed Extensions explicit boxing
```

Conversión boxing es implícita en Visual C++:

```cpp
Object ^o = 1024; // new syntax implicit boxing
```

El `__box` palabra clave proporciona un servicio fundamental en extensiones administradas, uno que no está presente por cuestiones de diseño de lenguajes como C# y Visual Basic: ofrece un vocabulario y el seguimiento de un controlador para manipular directamente una instancia de conversión boxing en el montón administrado. Por ejemplo, considere el siguiente programa pequeño:

```cpp
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

El código subyacente generado para las tres invocaciones de `WriteLine` Mostrar tipo de los distintos costos de acceso al valor de un valor con conversión boxing (agradecemos a Yves Dolce señalar estas diferencias), donde las líneas indicadas muestran la sobrecarga asociada a cada uno invocación.

```cpp
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

Pasando el tipo de valor con conversión boxing directamente a `Console::WriteLine` elimina la conversión boxing y la necesidad de invocar `ToString()`. (Por supuesto, hay la conversión boxing anterior para inicializar `br`, por lo que no logramos nada a menos que se pongan `br` funcione.

En la nueva sintaxis, la compatibilidad con tipos de valor con conversión boxing es considerablemente más elegante y está integrada en el sistema de tipos conservando su potencial. Por ejemplo, aquí es la traducción de pequeño programa anterior:

```cpp
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

[Tipos de valor y su comportamiento (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Cómo: Solicitar explícitamente la conversión boxing](../dotnet/how-to-explicitly-request-boxing.md)