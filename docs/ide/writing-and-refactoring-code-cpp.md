---
title: Editar y refactorizar código de C++ en Visual Studio
description: Use el editor de código de C++ en Visual Studio para dar formato al código, recorrerlo, entenderlo y refactorizarlo.
ms.date: 05/31/2019
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
ms.openlocfilehash: d4a74608a95df0fdd461f55d26fee97332a66aa8
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741628"
---
# <a name="edit-and-refactor-c-code-in-visual-studio"></a>Editar y refactorizar código de C++ en Visual Studio

Visual Studio proporciona varias herramientas que sirven para escribir, editar y refactorizar código.

##  <a name="intellisense"></a>IntelliSense

IntelliSense es una herramienta de finalización de código muy eficaz que sugiere símbolos y fragmentos de código automáticamente a medida que va escribiendo. C++ IntelliSense en Visual Studio se ejecuta en tiempo real y, al actualizar el código base, lo analiza y realiza recomendaciones. A medida que se escriben más caracteres, la lista de resultados recomendados se va acotando.

![Lista desplegable lista de miembros de C&#43;&#43;](../ide/media/cpp-statement-completion.png)

Algunos símbolos se omiten automáticamente para ayudar a acotar los resultados. Por ejemplo, al acceder a los miembros de un objeto de clase desde fuera de la clase, no podrá ver los miembros privados de forma predeterminada, ni los miembros protegidos (si no está en el contexto de una clase secundaria). El filtrado se puede ajustar con los botones de la parte inferior.

Después de elegir el símbolo de la lista desplegable, se puede autocompletar con las teclas **TAB** o **Entrar**, o con cualquiera de los otros caracteres de confirmación (de forma predeterminada: {}[]().,:;+-*/%&|^!=?@#\). Para agregar o quitar caracteres de esta lista, busque "IntelliSense" en **Inicio rápido** (Ctrl+Q) y elija la opción **Editor de texto > C/C++ > Avanzado**. La opción **Caracteres de confirmación de las listas de miembros** permite personalizar la lista con los cambios que quiera.

La opción **Modo de filtro de la lista de miembros** controla qué tipos de sugerencias de Autocompletar de IntelliSense van a aparecer. Esta opción está establecida de manera predeterminada en **Aproximada**. En una búsqueda aproximada, si tiene un símbolo llamado *MyAwesomeClass*, puede escribir "MAC" y buscar la clase entre las sugerencias de Autocompletar. El algoritmo aproximado establece un umbral mínimo que los símbolos deben cumplir para figurar en la lista. El filtrado **Inteligente** muestra todos los símbolos que contienen las subcadenas que coinciden con lo que ha escrito. El filtrado **Prefijo** busca cadenas que comiencen por lo que ha escrito.

Para obtener más información sobre C++ IntelliSense, vea [IntelliSense de Visual C++](/visualstudio/ide/visual-cpp-intellisense) y [Configurar un proyecto de C++ para IntelliSense](/visualstudio/ide/visual-cpp-intellisense-configuration).

## <a name="intellicode"></a>IntelliCode

IntelliCode es IntelliSense asistido por inteligencia artificial. Coloca al candidato más probable al principio de la lista de finalización. Las recomendaciones de IntelliCode se basan en miles de proyectos de código abierto de GitHub, cada uno con más de 100 estrellas. Cuando se combina en el contexto del código, la lista de finalización se adapta para promover prácticas habituales.

Al escribir C++, IntelliCode será de ayuda al usar bibliotecas muy conocidas, como la biblioteca estándar de C++. El contexto del código se usa para realizar las recomendaciones más útiles en primer lugar. En el siguiente ejemplo, la función miembro `size` se suele usar con la función `sort`, por lo que aparece al principio de la lista de resultados.

![IntelliCode de C&#43;&#43;](../ide/media/intellicode-cpp.png "IntelliCode de C++")

::: moniker range="vs-2019"

En Visual Studio 2019, IntelliCode está disponible como componente opcional en la carga de trabajo **Desarrollo para el escritorio con C++** . Para asegurarse de que IntelliCode está activo para C++, vaya a **Herramientas** > **Opciones** > **IntelliCode** > **General** y establezca **Modelo base de C++** en **Habilitado**.

::: moniker-end

::: moniker range="vs-2017"

En Visual Studio 2017, IntelliCode está disponible como una extensión en Visual Studio Marketplace.

::: moniker-end

## <a name="predictive-intellisense-experimental"></a>IntelliSense predictivo (experimental)

**IntelliSense predictivo** es una característica experimental que usa el reconocimiento contextual para limitar el número de resultados que aparecen en la lista desplegable de IntelliSense. El algoritmo hace uso de la coincidencia de tipos para mostrar únicamente aquellos resultados que coincidan con el tipo esperado. Siguiendo un ejemplo muy básico, si escribe `int x =` e invoca la lista desplegable de IntelliSense, solo verá números enteros o funciones que devuelven enteros. Esta característica está desactivada de forma predeterminada porque aún está en fase de desarrollo. Funciona mejor con símbolos globales; todavía no se admiten funciones miembro. Para activarla, escriba "Predictivo" en **Inicio rápido** o vaya a **Herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **Experimental** > **Habilitar IntelliSense predictivo**.

Para invalidar **IntelliSense predictivo** y mostrar una lista más larga, presione **Ctrl+J**. Si **IntelliSense predictivo** está activado, cuando se invoque **Ctrl+J** se quitará el filtro predictivo. Si se presiona **Ctrl+J** otra vez, se quita el filtro de accesibilidad de los resultados de la lista de miembros (cuando proceda). El botón ([+]) situado debajo de la lista desplegable de IntelliSense hace lo mismo que **Ctrl+J**. Mantenga el puntero sobre este botón para ver una información sobre herramientas sobre qué se está mostrando.

![IntelliSense predictivo de C&#43;&#43;](../ide/media/predictive-intellisense-cpp.png "IntelliSense predictivo")

La captura de pantalla anterior muestra varios botones debajo de la lista desplegable. Con ellos, se habilitan los filtros de IntelliSense para obtener distintos tipos de resultados:

- Variables y constantes
- Funciones
- Tipos
- Macros
- Enumeraciones
- Espacios de nombres

Un botón aparece solo si es relevante en la sesión actual de IntelliSense. Normalmente, no se ven todos los botones al mismo tiempo.

## <a name="template-intellisense"></a>IntelliSense para plantilla

Cuando el símbolo de intercalación está dentro de una definición de plantilla, aparece una **barra de plantillas** que le permite proporcionar argumentos de plantilla de ejemplo para IntelliSense. 

![IntelliSense para plantillas muestra las creaciones de instancias existentes en C&#43;&#43;](../ide/media/template-intellisense-cpp-1.png "IntelliSense para plantillas muestra las creaciones de instancias existentes")

Haga clic en el icono **<T>** para expandir o contraer la **barra de plantillas**. Haga clic en el icono de lápiz o haga doble clic en la **barra de plantillas** para abrir la ventana **Editar**. 

![IntelliSense para plantillas de C&#43; &#43;](../ide/media/template-intellisense-cpp-3.png "IntelliSense para plantillas")

Las modificaciones que se realizan en la ventana se aplican directamente al código fuente, así se ve su efecto en tiempo real. 

La barra de plantillas puede rellenar automáticamente los candidatos en función de las creaciones de instancias que haya en el código. Haga clic en **Agregar todas las creaciones de instancias existentes** para ver una lista de todos los argumentos concretos que se han usado para crear instancias de la plantilla a lo largo del código base.

![Lista de resultados de IntelliSense para plantillas de C&#43;&#43;](../ide/media/template-intellisense-cpp-2.png "Lista de resultados de IntelliSense para plantillas")

Una ventana en la parte inferior del editor señala dónde se ha detectado cada creación de instancias y cuáles han sido sus argumentos.

![Mapa de creaciones de instancias de IntelliSense para plantillas de C&#43;&#43;](../ide/media/template-intellisense-cpp-4.png "Mapa de creaciones de instancias de IntelliSense para plantillas")

La información de la **barra de plantillas** se considera como específica del usuario. Se almacena en la carpeta .vs y no se confirma en el control de código fuente.

##  <a name="error-squiggles-and-quick-fixes"></a>Subrayados ondulados de error y soluciones rápidas

Si el editor detecta problemas con el código, agregará subrayados ondulados de color debajo del problema. Un subrayado ondulado de color rojo señala código que no se va a compilar. El subrayado ondulado de color verde señala otros tipos de problemas, que pueden llegar a ser graves. Puede abrir la ventana **Lista de errores** para obtener más información sobre los problemas.

En algunos tipos de errores, así como en patrones de programación comunes, el editor ofrecerá una **corrección rápida** en forma de bombilla, que aparece cuando se mantiene el puntero sobre el subrayado ondulado. Haga clic en la flecha abajo para ver las sugerencias. 

En el siguiente ejemplo, hay un elemento `vector` declarado, pero no se encontró ninguna definición, por lo que el editor sugiere incluir el archivo de encabezado necesario:

![Corrección rápida de C&#43;&#43;](../ide/media/quick-fix-for-header-cpp.png "Corrección rápida de C++")

El editor también ofrece soluciones rápidas en algunas oportunidades de refactorización. Por ejemplo, si declara una clase en un archivo de encabezado, Visual Studio propondrá crear una definición para ella en un archivo .cpp aparte. 

![Corrección rápida de C&#43;&#43;](../ide/media/quick-fix.png "Corrección rápida de C++")

## <a name="change-tracking"></a>Seguimiento de cambios

Cada vez que haga un cambio en un archivo, aparecerá una barra amarilla a la izquierda que informa de que se han realizado cambios sin guardar. Cuando guarde el archivo, la barra cambiará a color verde. Las barras verde y amarilla siguen apareciendo mientras el documento esté abierto en el editor. Señalan los cambios realizados desde que el documento se abrió por última vez.

![Seguimiento de cambios de C&#43;&#43;](../ide/media/change-tracking-cpp.png "Seguimiento de cambios")

## <a name="move-code"></a>Mover código

Las líneas de código se pueden subir y bajar; para ello, solo tiene que seleccionarlas manteniendo la tecla Alt presionada y presionar las teclas de dirección **arriba/abajo**.

##  <a name="insert-snippets"></a>Insertar fragmentos de código

Un fragmento de código es una parte de código fuente predefinida. Haga clic con el botón derecho en un único punto o en el texto seleccionado para insertar un fragmento de código o rodear el texto seleccionado con el fragmento de código. La siguiente ilustración muestra los tres pasos necesarios para envolver una instrucción seleccionada con un bucle for. Las partes resaltadas en amarillo de la imagen final son campos que se pueden editar y a los que puede acceder con la tecla TAB. Para obtener más información, vea [Fragmentos de código](/visualstudio/ide/code-snippets).

![Lista desplegable Insertar fragmento de código de C&#43;&#43;](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

##  <a name="add-class"></a>Agregar clase

Agregue una nueva clase desde el menú **Proyecto** o desde el menú contextual del **Explorador de soluciones**:

![Agregar nueva clase en C&#43;&#43;](../ide/media/vs2017-add-class.png "vs2015_cpp_add_class")

También puede usar el Asistente para clases para modificar o examinar una clase existente.

![Asistente para clases de C&#43;&#43;](../ide/media/vs2017-class-wizard.png)

Para obtener más información, vea [Agregar funcionalidad con los asistentes para código (C++)](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="refactoring"></a>Refactorización

Las refactorizaciones están disponibles bajo el menú contextual Acción rápida, o bien haciendo clic en una [bombilla](/visualstudio/ide/perform-quick-actions-with-light-bulbs) en el editor.  Algunas se encuentran en el menú **Editar > Refactorizar**.  Entre ellas se incluyen:

* [Cambiar nombre](refactoring/rename.md)
* [Extraer función](refactoring/extract-function.md)
* [Implementar virtuales puras](refactoring/implement-pure-virtuals.md)
* [Crear declaración o definición](refactoring/create-declaration-definition.md)
* [Mover definición de función](refactoring/move-definition-location.md)
* [Convertir en literal de cadena sin formato](refactoring/convert-to-raw-string-literal.md)
* [Cambiar firma](refactoring/change-signature.md)

## <a name="code-style-enforcement-with-clangformat-and-editorconfig"></a>Aplicación de estilo de código con ClangFormat y EditorConfig

Visual Studio 2017 y las versiones posteriores incluyen compatibilidad integrada con [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html), una conocida utilidad de formato de código para C++ basada en Clang/LLVM. Escriba "ClangFormat" en [Inicio rápido](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box) para configurarla para que use uno de estos formatos comunes:

- LLVM
- Google
- Chromium
- Mozilla
- WebKit
- Programa para la mejora

También puede proporcionar su propio archivo .clang-format o _clang-format para aplicar reglas personalizadas a todos los archivos de código del mismo nivel o por debajo.

Estos archivos se pueden compartir fácilmente a través del control de código fuente, lo que permite que todo el equipo de desarrollo use las mismas convenciones de código.

![Formato de Clang de C&#43;&#43;](../ide/media/clang-format-cpp.png "Formato de Clang")

Visual Studio 2017 y las versiones posteriores también admiten [EditorConfig](https://editorconfig.org/), que funciona de forma similar, si bien ClangFormat tiene más opciones de estilo que EditorConfig, incluido reglas que son específicas de C++. Con **EditorConfig** se crean archivos **.editorconfig** y se ponen en diferentes carpetas del código base para especificar estilos de código aplicables a esas carpetas y sus subcarpetas. Un archivo **.editorconfig** sustituye cualquier otro archivo **.editorconfig** que haya en las carpetas principales, y sobrescribe cualquier configuración de formato que se haya establecido a través de **Herramientas** > **Opciones**. Se pueden establecer reglas de tabulaciones frente a espacios o tamaños de sangría, entre otras muchas cosas. Para obtener más información, vea [Crear opciones de configuración del editor personalizadas y portátiles con EditorConfig](/visualstudio/ide/create-portable-custom-editor-options).

## <a name="other-formatting-options"></a>Otras opciones de formato

El cuadro de búsqueda **Inicio rápido** constituye la forma más rápida de encontrar una configuración o una herramienta. Se encuentra en el menú principal. Solo tiene que empezar a escribir y la lista de autocompletar filtrará los resultados.

![Inicio rápido de Visual Studio](../ide/media/vs2015_cpp_quick_launch.png "Inicio rápido")

Para establecer opciones de formato, como sangrías, finalización de llave y uso de colores, escriba "Formato de C++" en la ventana **Inicio rápido**.

![Opciones de formato de C++](media/cpp-formatting-options.png)

Encontrará otras opciones de formato en **Editar** > **Avanzado** en el menú principal.

![Opciones de edición avanzadas de C++](media/edit-advanced-cpp.png)

Las opciones para habilitar y configurar características de edición específicas de C++ se encuentran en **Herramientas** > **Opciones** > **Editor de texto** > **C/C++** . Después de elegir la opción que quiere establecer, puede obtener más ayuda si presiona **F1** cuando el cuadro de diálogo tenga el foco. Para acceder a las opciones de formato de código generales, escriba `Editor C++` en **Inicio rápido**.

![Herramientas > Opciones en Visual Studio](../ide/media/tools-options.png "Opciones del editor")

Las características experimentales, que se podrían incluir o no en una versión futura de Visual Studio, se encuentran en el cuadro de diálogo [Editor de texto C++ Experimental](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental). En Visual Studio 2017 y versiones posteriores, **IntelliSense predictivo** se puede habilitar en este cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Lectura y reconocimiento de código C++](read-and-understand-code-cpp.md)</br>
[Navegación en el código de C++ en Visual Studio](navigate-code-cpp.md)</br>
[Colaborar con Live Share para C++](live-share-cpp.md)