---
title: 'Inicio rápido: Análisis de código para C/C++'
description: Ejecute el análisis estático en código C++ en Visual Studio para detectar problemas y defectos de codificación comunes.
ms.date: 04/08/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis, C/C++
ms.openlocfilehash: 43866564915ac84d227ccbf347280efe59e33351
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370572"
---
# <a name="quickstart-code-analysis-for-cc"></a>Inicio rápido: Análisis de código para C/C++

Se puede mejorar la calidad de la aplicación si se analiza con regularidad el código de C o C++. El análisis de código puede ayudarle a encontrar problemas comunes y violaciones de las buenas prácticas de programación. Además, encuentra defectos que son difíciles de descubrir a través de pruebas. Sus advertencias difieren de los errores y advertencias del compilador: busca patrones de código específicos que se sabe que causan problemas. Es decir, código que es válido, pero que todavía podría crear problemas, ya sea para usted o para otras personas que usan el código.

## <a name="configure-rule-sets-for-a-project"></a>Configurar conjuntos de reglas para un proyecto

1. En el **Explorador**de soluciones , abra el menú contextual del nombre del proyecto y, a continuación, elija **Propiedades**.

1. Opcionalmente, en las listas **Configuración** y **Plataforma,** elija la configuración de compilación y la plataforma de destino.

1. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, active la casilla Habilitar análisis de **código en compilación.** También puede ejecutar el análisis de código manualmente abriendo el menú **Analizar** y, a continuación, **seleccionando Ejecutar análisis** de código en *ProjectName* o **Ejecutar análisis**de código en archivo .

1. Elija el conjunto de [reglas](using-rule-sets-to-specify-the-cpp-rules-to-run.md) que desea utilizar o cree un conjunto de [reglas personalizado.](using-rule-sets-to-specify-the-cpp-rules-to-run.md#to-create-a-rule-set-in-a-text-editor) Si usa LLVM/clang-cl, consulte Uso de [Clang-Tidy en Visual Studio](../code-quality/clang-tidy.md) para configurar las opciones de análisis de Clang-Tidy.

### <a name="standard-cc-rule-sets"></a>Conjuntos de reglas estándar C/C++

Visual Studio incluye estos conjuntos estándar de reglas para código nativo:

| Conjunto de reglas | Descripción |
|--|--|
| **Reglas aritméticas de comprobación de núcleo C++** | Estas reglas aplican comprobaciones relacionadas con [operaciones aritméticas de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements). |
| **Reglas de límites de comprobación de núcleo C++** | Estas reglas aplican el [perfil Límites de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile). |
| **Reglas de clase de comprobación básica C++** | Estas reglas aplican comprobaciones relacionadas con [las clases de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-classes-and-class-hierarchies). |
| **Reglas de simultaneidad de cheques principales C++** | Estas reglas aplican comprobaciones relacionadas con [la simultaneidad de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cpcon-concurrency). |
| **C++ Reglas de Control de Núcleo Const** | Estas reglas aplican [comprobaciones relacionadas con las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability). |
| **Reglas de declaración de comprobación básica C++** | Estas reglas aplican comprobaciones relacionadas con [declaraciones de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i-interfaces). |
| **Reglas de la enumeración de comprobación de núcleo C++** | Estas reglas aplican [comprobaciones relacionadas con la enumeración de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-enum). |
| **C++ Reglas experimentales de comprobación básica** | Estas reglas recopilan algunos controles experimentales. Eventualmente, esperamos que estas comprobaciones se muevan a otros conjuntos de reglas o se eliminen por completo. |
| **Reglas de función de comprobación básica C++** | Estas reglas aplican comprobaciones relacionadas con [funciones de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f-functions). |
| **Reglas de Comprobación de Núcleo C++ GSL** | Estas reglas aplican comprobaciones relacionadas con la Biblioteca de soporte de [directrices de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-gsl). |
| **Reglas de por vida de C++ Core Check** | Estas reglas aplican el [perfil Lifetime de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prolifetime-lifetime-safety-profile). |
| **Reglas de puntero del propietario de comprobación principal C++** | Estas reglas aplican comprobaciones de administración de recursos relacionadas con [el propietario&lt;T&gt; de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management). |
| **C++ Core Check Raw Pointer Rules** | Estas reglas aplican comprobaciones de administración de recursos relacionadas con [punteros sin procesar de las Directrices principales de C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management) |
| **Reglas de comprobación básica C++** | Estas reglas aplican un subconjunto de las comprobaciones de las [Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c-core-guidelines). Utilice este conjunto de reglas para incluir todas las reglas de comprobación de núcleo de C++, excepto los conjuntos de reglas Enum y Experimental. |
| **C++ Reglas de puntero compartido de comprobación principal** | Estas reglas aplican comprobaciones de administración de recursos relacionadas con tipos con semántica de puntero compartido de las Directrices principales de [C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management) |
| **Reglas de STL de comprobación básica C++** | Estas reglas aplican comprobaciones relacionadas con la biblioteca de [plantillas estándar (STL) de C++ de las directrices principales de C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-stdlib) |
| **Reglas de estilo de comprobación de núcleo C++** | Estas reglas aplican comprobaciones relacionadas con el uso de [expresiones e instrucciones de las Directrices básicas de C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es-expressions-and-statements) |
| **Reglas de tipo de comprobación básica C++** | Estas reglas aplican el [perfil Tipo de las Directrices básicas de C++](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile). |
| **C++ Core Check Reglas de puntero único** | Estas reglas aplican comprobaciones de administración de recursos relacionadas con tipos con semántica de puntero única de las directrices principales de [C++.](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management) |
| **Reglas de comprobación de simultaneidad** | Estas reglas aplican un conjunto de comprobaciones de patrón de simultaneidad Win32 en C++. |
| **Reglas de simultaneidad** | Agrega reglas de simultaneidad de Directrices principales de C++ a reglas de comprobación de **simultaneidad**. |
| **Reglas mínimas nativas de Microsoft** | Estas reglas se centran en los problemas más críticos del código nativo, incluidos los posibles agujeros de seguridad y los bloqueos de aplicaciones. Se recomienda incluir este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para sus proyectos nativos. |
| **Reglas recomendadas nativas de Microsoft** | Estas reglas se centran en los problemas más críticos y comunes en el código nativo. Estos problemas incluyen posibles agujeros de seguridad y bloqueos de aplicaciones. Se recomienda incluir este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para sus proyectos nativos. Este conjunto de reglas está diseñado para funcionar con Visual Studio Professional y versiones posteriores. Incluye todas las reglas de **Microsoft Native Minimum Rules**. |

Visual Studio incluye estos conjuntos estándar de reglas para código administrado:

| Conjunto de reglas | Descripción |
|--|--|
| **Reglas básicas de corrección de Microsoft** | Estas reglas se centran en errores lógicos y comunes cometidos en el uso de API de marco de trabajo. Incluya este conjunto de reglas para ampliar la lista de advertencias emitidas por las reglas mínimas recomendadas. |
| **Reglas de la Guía básica de diseño de Microsoft** | Estas reglas se centran en exigir procedimientos recomendados para que el código sea fácil de comprender y de usar. Incluya este conjunto de reglas si el proyecto incluye código de bibliotecas o si desea exigir procedimientos recomendados para que el código sea fácil de mantener. |
| **Reglas de corrección extendida de Microsoft** | Estas reglas se expanden en las reglas básicas de corrección para maximizar la lógica notificada y los errores de uso del marco de trabajo. Se pone especial énfasis en escenarios específicos como la interoperabilidad COM y las aplicaciones móviles. Considere incluir este conjunto de reglas si alguno de estos escenarios es aplicable a su proyecto o para buscar problemas adicionales del proyecto. |
| **Reglas de la Guía de diseño ampliada de Microsoft** | Estas reglas amplían las reglas básicas de las directrices de diseño para maximizar los problemas de usabilidad y mantenimiento notificados. Se pone especial énfasis en las directrices de nomenclatura. Considere incluir este conjunto de reglas si el proyecto incluye código de bibliotecas o si desea exigir los más altos estándares para escribir código fácil de mantener. |
| **Reglas de globalización de Microsoft** | Estas reglas se centran en problemas que impiden que los datos de la aplicación se muestren correctamente cuando se usan en diferentes idiomas, configuraciones regionales y referencias culturales. Incluya este conjunto de reglas si la aplicación está localizada o globalizada. |
| **Reglas mínimas administradas de Microsoft** | Estas reglas se centran en los problemas más graves del código para los que el análisis del mismo es la solución más precisa.  Estas reglas son pocas y están destinadas a ejecutarse solamente en ediciones limitadas de Visual Studio.  Use MinimumRecommendedRules.ruleset con otras ediciones de Visual Studio. |
| **Reglas recomendadas administradas de Microsoft** | Estas reglas se centran en los problemas más críticos del código. Estos problemas incluyen posibles agujeros de seguridad, bloqueos de aplicaciones y otros errores importantes de lógica y diseño. Le recomendamos que incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para sus proyectos. |
| **Reglas mínimas mixtas de Microsoft (C++ /CLR)** | Estas reglas se centran en los problemas más críticos de los proyectos de C++ que admiten Common Language Runtime. Estos problemas incluyen posibles agujeros de seguridad, bloqueos de aplicaciones y otros errores importantes de lógica y diseño. Se recomienda incluir este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para los proyectos de C++ que admitan Common Language Runtime. |
| **Reglas recomendadas de Microsoft Mixed (C++ /CLR)** | Estas reglas se centran en los problemas más comunes y críticos de los proyectos de C++ que admiten Common Language Runtime. Estos problemas incluyen posibles agujeros de seguridad, bloqueos de aplicaciones y otros errores importantes de lógica y diseño. Este conjunto de reglas está diseñado para su uso en la edición de Visual Studio Professional y superior. |
| **Reglas de seguridad de Microsoft** | Este conjunto de reglas contiene todas las reglas de seguridad de Microsoft. Incluya este conjunto de reglas para maximizar el número de posibles problemas de seguridad que se detectan. |

Para incluir todas las reglas:

| Conjunto de reglas | Descripción |
|--|--|
| **Microsoft All Rules** | Este conjunto de reglas contiene todas las reglas. Si se ejecuta este conjunto de reglas, puede dar lugar a un gran número de advertencias. Use este conjunto de reglas para obtener una imagen completa de todos los problemas del código. Puede ayudarle a decidir cuáles de los conjuntos de reglas más centrados son los más adecuados para ejecutar se ejecutan para sus proyectos. |

## <a name="run-code-analysis"></a>Ejecutar análisis de código

En la página **Análisis** de código del cuadro de diálogo Propiedades del proyecto, puede configurar el análisis de código para que se ejecute cada vez que compile el proyecto. También se puede ejecutar el análisis de código de forma manual.

Para ejecutar el análisis de código en una solución:

- En el menú **Compilar** , elija **Ejecutar análisis de código en la solución**.

Para ejecutar el análisis de código en proyecto:

1. En el Explorador de soluciones, seleccione el nombre del proyecto.

1. En el menú **Generar** , elija **Ejecutar análisis de código en** el nombre del *proyecto*.

Para ejecutar el análisis de código en un archivo:

1. En el Explorador de soluciones, seleccione el nombre del archivo.

1. En el menú **Generar,** elija **Ejecutar análisis** de código en archivo o pulse **Ctrl+Mayús+Alt+F7**.

   La solución o proyecto se compila y se ejecuta el análisis de código. Los resultados aparecen en la ventana Lista de errores.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizar y resolver las advertencias del análisis de código

La ventana Lista de errores muestra las advertencias de análisis de código encontradas. Los resultados se muestran en una tabla. Si hay más información disponible sobre una advertencia determinada, la primera columna contiene un control de expansión. Elija que se expanda la pantalla para obtener información adicional sobre el problema. Cuando es posible, el análisis de código muestra los números de línea y la lógica de análisis que condujeron a la advertencia.

Para obtener información detallada acerca de la advertencia, incluidas las posibles soluciones al problema, elija el identificador de advertencia en la columna Código para mostrar su artículo de ayuda en línea correspondiente.

Haga doble clic en una advertencia para mover el cursor a la línea de código que causó la advertencia en el editor de código de Visual Studio. O bien, pulse Intro en la advertencia seleccionada.

Cuando haya entendido el problema, podrá resolverlo en el código. A continuación, vuelva a ejecutar el análisis de código para asegurarse de que la advertencia ya no aparece en la lista de errores.

## <a name="create-work-items-for-code-analysis-warnings"></a>Crear elementos de trabajo para advertencias de análisis de código

La característica de seguimiento de elemento de trabajo permite registrar errores desde Visual Studio. Para usar esta característica, debe conectarse a una instancia de VSTS Server (anteriormente, Team Foundation Server).

### <a name="to-create-a-work-item-for-one-or-more-cc-code-warnings"></a>Para crear un elemento de trabajo para una o más advertencias de código de C/C++

1. En la lista de errores, expanda y seleccione las advertencias

1. En el menú contextual de las advertencias, elija **Crear elemento de trabajo**y, a continuación, elija el tipo de elemento de trabajo.

1. Visual Studio crea un único elemento de trabajo para las advertencias seleccionadas y muestra el elemento de trabajo en una ventana de documento del IDE.

1. Agregue cualquier información adicional y, a continuación, elija **Save Work Item**.

## <a name="search-and-filter-code-analysis-results"></a>Resultados de análisis de código de búsqueda y filtro

Puedes buscar en las listas largas de mensajes de advertencia y filtrar las advertencias en las soluciones de varios proyectos.

- **Para filtrar las advertencias por título o ID**de advertencia: escriba la palabra clave en el cuadro Lista de errores de búsqueda.

- **Para filtrar las advertencias por gravedad:** De forma predeterminada, a los mensajes de análisis de código se les asigna una gravedad de **Advertencia**. Puede asignar la gravedad de uno o varios mensajes como **Error** en un conjunto de reglas personalizado. En la columna **Gravedad** de la **lista**de errores , elija la flecha desplegable y, a continuación, el icono de filtro. Elija **Advertencia** o **Error** para mostrar solo los mensajes a los que se asigna la gravedad respectiva. Elija **Seleccionar todo** para mostrar todos los mensajes.

## <a name="see-also"></a>Consulte también

- [Análisis de código para C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
