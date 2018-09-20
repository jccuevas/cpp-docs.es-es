---
title: Referencia del lenguaje C++ | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fdf0980b8994c313349fd30f05e667b9c0cd461
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377103"
---
# <a name="c-language-reference"></a>Referencia del lenguaje C++

Esta referencia explica el lenguaje de programación C++ tal como se implementa en Microsoft Visual C++. La organización se basa en *The Annotated C++ Reference Manual* de Margaret Ellis y Bjarne Stroustrup y en los estándares de internacionales de C++ de ANSI/ISO (ISO/IEC FDIS 14882). Se incluyen las implementaciones específicas de Microsoft de las características del lenguaje C++.

Para obtener información general de las prácticas de programación de C++ moderno, consulte [Bienvenido a C++](welcome-back-to-cpp-modern-cpp.md).

Consulte las tablas siguientes para encontrar rápidamente una palabra clave o un operador:

- [Palabras clave de C++](../cpp/keywords-cpp.md)

- [Operadores de C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>En esta sección

[Convenciones léxicas](../cpp/lexical-conventions.md)<br/>
Elementos léxicos fundamentales de un programa de C++: tokens, comentarios, operadores, palabras clave, signos de puntuación, literales. También, traducción de archivos, prioridad o asociatividad de los operadores.

[Conceptos básicos](../cpp/basic-concepts-cpp.md)<br/>
Ámbito, vinculación, inicio y finalización del programa, clases de almacenamiento y tipos.

[Conversiones estándar](../cpp/standard-conversions.md)<br/>
Conversiones de tipos entre tipos integrados o “fundamentales". También, conversiones aritméticas y conversiones entre tipos de puntero, referencia y puntero a miembro.

[Operadores, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
Operadores de C++.

[Expresiones](../cpp/expressions-cpp.md)<br/>
Tipos de expresiones, semántica de expresiones, temas de referencia sobre operadores, conversión y operadores de conversión, información de tipos en tiempo de ejecución.

[Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
Una técnica de programación que define implícitamente una clase de objeto de función y crea un objeto de función de ese tipo de clase.

[Instrucciones](../cpp/statements-cpp.md)<br/>
Instrucciones de expresión, null, compuestas, de selección, de iteración, de salto y de declaración.

[Declaraciones y definiciones](declarations-and-definitions-cpp.md)<br/>
Especificadores de clase de almacenamiento, las definiciones de función, inicializaciones, enumeraciones, **clase**, **struct**, y **unión** declaraciones, y **(typedef)**  declaraciones. Además, **inline** funciones, **const** palabra clave, los espacios de nombres.

[Las clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md)<br/>
Introducción a las clases, estructuras y uniones. Además, las funciones de miembro, las funciones miembro especiales, los miembros de datos, campos de bits, **esto** puntero, clases anidadas.

[Clases derivadas](../cpp/inheritance-cpp.md)<br/>
Herencia sencilla y múltiple, **virtual** funciones, clases base múltiples, **abstracta** clases, las reglas de ámbito. Además, el **__super** y **__interface** palabras clave.

[Control de acceso a miembros](../cpp/member-access-control-cpp.md)<br/>
Controlar el acceso a los miembros de clase: **pública**, **privada**, y **protegido** palabras clave. Funciones y clases friend.

[La sobrecarga](operator-overloading.md)<br/>
Operadores sobrecargados, reglas de sobrecarga del operador.

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)<br/>
Control de excepciones de C++, control estructurado de excepciones (SEH), palabras clave usadas para escribir instrucciones de control de excepciones.

[Aserción y mensajes proporcionados por el usuario](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error` Directiva, el **static_assert** palabra clave, el `assert` macro.

[Templates](../cpp/templates-cpp.md) (Plantillas [C++])<br/>
Especificaciones de plantilla, plantillas de función, plantillas de clase, **typename** palabra clave, plantillas y macros, plantillas y punteros inteligentes.

[Control de eventos](../cpp/event-handling.md)<br/>
Declaración de eventos y controladores de eventos.

[Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md)<br/>
Modificadores específicos de Microsoft C++. La memoria de direccionamiento, convenciones de llamada, **naked** funciones, atributos extendidos de clase de almacenamiento (**__declspec**), **__w64**.

[Ensamblador insertado](../assembler/inline/inline-assembler.md)<br/>
Usando el lenguaje de ensamblado y C++ en **__asm** bloques.

[Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)<br/>
Una referencia a las clases específicas de Microsoft y funciones globales utilizadas para admitir tipos COM.

[Extensiones para Microsoft](../cpp/microsoft-extensions.md)<br/>
Extensiones de Microsoft a C++.

[Comportamiento no estándar](../cpp/nonstandard-behavior.md)<br/>
Información sobre el comportamiento no estándar del compilador de Visual C++.

[Aquí está otra vez C++](welcome-back-to-cpp-modern-cpp.md)<br/>
Información general sobre procedimientos recomendados para escribir programas seguros, correctos y eficaces de programación moderna de C++.

## <a name="related-sections"></a>Secciones relacionadas

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)<br/>
Material de referencia sobre cómo usar Visual C++ orientado a Common Language Runtime.

[Referencia de compilación de C/C++](../build/reference/c-cpp-building-reference.md)<br/>
Opciones del compilador, opciones del vinculador y otras herramientas de compilación.

[Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Material de referencia sobre instrucciones pragma, directivas de preprocesador, macros predefinidas y el preprocesador.

[Bibliotecas de Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Una lista de vínculos a las páginas de inicio de referencia para las diferentes bibliotecas de Visual C++.

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C](../c-language/c-language-reference.md)