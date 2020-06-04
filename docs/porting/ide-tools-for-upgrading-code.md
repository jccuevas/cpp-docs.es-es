---
title: Herramientas del IDE de Visual Studio para C++ actualizar el código
description: El C++ editor de código y las herramientas de análisis de código de Visual Studio le C++ ayudan a modernizar la base de código.
ms.date: 11/13/2019
ms.topic: conceptual
ms.openlocfilehash: 409fc0a2fa6cd39c7751dc34b20b231ffbea3956
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416149"
---
# <a name="visual-studio-ide-tools-for-upgrading-c-code"></a>Herramientas del IDE de Visual Studio para C++ actualizar el código

Visual Studio le ayuda a actualizar C++ el código heredado con opciones de compilador, advertencias de análisis de código y características del editor, como correcciones rápidas, información rápida y la barra de desplazamiento mejorada. El término "código heredado" hace referencia a cualquiera de estas categorías:

- Código previamente permitido por el compilador C++ de Microsoft (MSVC), pero que nunca se ajusta C++ al estándar.

   Para actualizar el código de MSVC no compatible anterior, active la opción del compilador [/permissive-](../build/reference/permissive-standards-conformance.md) . Todas las instancias de los usos no conformes se subrayan con líneas onduladas rojas en el editor de código. Los mensajes de error de la ventana de **lista de errores** incluyen una recomendación sobre cómo corregir el error. Haga clic en el código de error para ir a su página de ayuda en la documentación de. Si no es práctico corregir todos los errores a la vez, puede actualizar el código no compatible en fases activando la opción **permissive** , corrigiendo algunos errores y volviendo a desactivar la opción. El código se compilará con las nuevas mejoras y podrá volver atrás y corregir los problemas restantes en otro momento. Vea la página [/permissive-](../build/reference/permissive-standards-conformance.md) para ver ejemplos de código MSVC no compatible.

- Código que se permitía en una versión anterior del C++ estándar, pero que quedó en desuso o se quitó en una versión posterior.

   Para actualizar a un estándar de lenguaje más reciente, [ C++ ](../build/reference/std-specify-language-standard-version.md) establezca la opción de lenguaje estándar en el estándar deseado y corrija los errores de compilación que se produzcan. En general, se recomienda establecer el estándar de lenguaje en [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md). Los errores que se producen al actualizar a un estándar más reciente no están relacionados con los errores que se producen al usar la opción **permissive-** .

- Código que se ajusta a todas las versiones del estándar, pero que ya no se considera el procedimiento recomendado C++en moderno.

   Para identificar el código en el que se recomiendan los cambios, ejecute el [análisis de código](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="open-and-convert-a-legacy-project"></a>Abrir y convertir un proyecto heredado

Si el proyecto heredado se basa en una versión anterior de Visual Studio, puede abrirlo en Visual Studio 2017 o Visual Studio 2019. Visual Studio lo convierte automáticamente en el esquema del proyecto actual con compatibilidad con todas las características más recientes del compilador y del IDE.

![Actualizar un proyecto](media/upgrade-dialog-v142.png "Actualizar un proyecto")

Para obtener más información, [vea C++ actualizar proyectos desde versiones anteriores de Visual Studio](upgrading-projects-from-earlier-versions-of-visual-cpp.md).

## <a name="search-the-code-base"></a>Buscar en el código base

La actualización de una base de código a menudo implica la búsqueda en varios archivos. Para buscar cualquier elemento en la base de código, presione **Ctrl + T** para abrir el cuadro de búsqueda **ir a todo** .

![Ir a todo](media/go-to-all.png "Ir a todo")

Para restringir el ámbito de búsqueda, escriba uno de los filtros de 1 letra, seguido de un espacio y de lo que busca.

## <a name="error-list"></a>Lista de errores

Después de establecer el estándar C++ del lenguaje deseado y cualquier otra opción del compilador ( **propiedades** del**proyecto** >  > **General**), presione **Ctrl + Mayús + B** para compilar el proyecto. Puede esperar ver algunos errores y advertencias en forma de subrayado ondulado de color rojo en varios lugares del código. Los errores también aparecen en el **lista de errores**. Para obtener más información sobre un error concreto, haga clic en el código de error para ir a la página de ayuda en la documentación de. Los códigos de error que comienzan por una "C" son errores del compilador. Los códigos que comienzan por "MSB" son errores de MSBuild que indican un problema con la configuración del proyecto.

![Errores del compilador y de MSBuild en Lista de errores](media/compiler-error-list.png "Errores del compilador y de MSBuild en Lista de errores")

## <a name="document-health-indicator"></a>Indicador de estado de documento

El indicador de estado de documento en la parte inferior del editor muestra el número de errores y advertencias en el documento actual y le permite navegar directamente desde una advertencia o un error hasta el siguiente.

![Indicador de estado de documento](media/document-health-indicator.png "Indicador de estado de documento")

En muchos casos, puede encontrar más información sobre un error específico en la documentación sobre el historial de cambios y mejoras de conformidad de Visual Studio.

- [C++mejoras de conformidad](../overview/cpp-conformance-improvements.md)
- [Historial C++ de cambios visuales 2003-2015](visual-cpp-change-history-2003-2015.md)
- [Información general sobre posibles problemas de actualización](overview-of-potential-upgrade-issues-visual-cpp.md)

## <a name="use-code-analysis-to-modernize-your-code"></a>Usar el análisis de código para modernizar el código

Al realizar la actualización, se recomienda ejecutar el análisis de código en el proyecto para que el código se ajuste a las reglas recomendadas nativas de Microsoft. Estas reglas son una combinación de reglas definidas por Microsoft y un subconjunto de las [ C++ directrices básicas](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines). Al hacerlo, reducirá en gran medida o eliminará los orígenes comunes de errores y, al mismo tiempo, el código será más legible y, por lo tanto, será más fácil de mantener. El análisis de código con las reglas recomendadas nativas de Microsoft está habilitado de forma predeterminada. Puede habilitar reglas adicionales en > **propiedades** del **proyecto** > **análisis de código**. El código que infringe una de las reglas se marca como una advertencia y está subrayado con una línea ondulada de color verde en el editor de código. Mantenga el mouse sobre la línea ondulada para ver la información sobre herramientas de **QuickInfo** que describe el problema.

![Información sobre análisis de código](media/code-analysis-tooltip.png "ADVERTENCIA de análisis de código")

Haga clic en el icono de filtro en la columna **código** para elegir las advertencias que se muestran.

![Filtros de análisis de código en Lista de errores](media/code-analysis-filter.png "Filtros de análisis de código en Lista de errores")

Los errores y advertencias del análisis de código también aparecen en el **lista de errores** igual que los errores del compilador.

![Advertencias de análisis de código en Lista de errores](media/code-analysis-error-list.png "Advertencias de análisis de código en Lista de errores")

Puede cambiar qué reglas están activas y crear conjuntos de reglas personalizadas. Para obtener más información sobre el uso del análisis de código, vea [análisisC++ de código para C/Overview](/cpp/code-quality/code-analysis-for-c-cpp-overview).

## <a name="use-quick-actions-to-modernize-code"></a>Uso de acciones rápidas para modernizar código

El editor de código proporciona acciones rápidas para algunas recomendaciones comunes. Cuando aparezca el icono de bombilla, puede hacer clic en él para ver las acciones rápidas disponibles.

### <a name="convert-macros-to-constexpr-functions"></a>Convertir macros en funciones constexpr

En la imagen siguiente se muestra el uso de una macro denominada `AVERAGE`, que tiene la coloración semántica predeterminada. La imagen también muestra la información sobre herramientas de QuickInfo que se muestra cuando el cursor del mouse se desplaza sobre ella:

![Expansión de macros QuickInfo](media/macro-expansion-quick-info.png "QuickInfo la expansión de macro ToolTip")

Dado que no se recomienda el uso de macros en moderno C++, Visual Studio facilita la conversión de macros en funciones **constexpr** :

1. Haga clic con el botón derecho en `AVERAGE` y elija **ir a definición**.
2. Haga clic en el icono de destornillador y elija **convertir macro en constexpr** .

   ![Macro de acción rápida a constexpr](media/quick-action-macro-to-constexpr.png "Macro de acción rápida a constexpr")

La macro se convierte como se muestra a continuación:

![constexpr (función)](media/constexpr-function.png "constexpr (función)")

Y la llamada a `AVERAGE` ahora está coloreada como una llamada de función y el Información rápida muestra el tipo deducido de la función:

![llamada a la función constexpr](media/constexpr-function-call.png "llamada a la función constexpr")

### <a name="initialize-variables"></a>Inicialización de variables

Las variables no inicializadas pueden contener valores aleatorios que conducen a errores graves. El análisis de código marca estas instancias y el editor proporciona una acción rápida:

![Inicializar variable](media/init-variable.png "Iniciar acción rápida de variable")

### <a name="convert-to-raw-string-literal"></a>Convertir en literal de cadena sin formato

Los literales de cadena sin formato son menos propensos a errores y más cómodos de escribir que las cadenas con caracteres de escape incrustados. Haga clic con el botón derecho en una cadena y elija **acciones rápidas** para convertirla en un literal de cadena sin formato.

![Literal de cadena sin formato](media/raw-string-literal.png "Literal de cadena sin formato")

La cadena se convierte en: `R"(C:\Users\bjarnes\demo\output.txt)"`.
