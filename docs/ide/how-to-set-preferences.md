---
title: Establezca sus preferencias de codificación C++ en Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365391"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Establezca sus preferencias de codificación C++ en Visual Studio

Puede hacer que su experiencia de codificación C++ sea más conveniente, productiva y placentera personalizando Visual Studio. Puede:

- Personalice los menús y las barras de herramientas.
- Organice el diseño de la ventana.
- Establezca temas de color.
- Especifique las reglas de formato C+++, incluidos varios estilos de ClangFormat.
- Crear métodos abreviados de teclado personalizados.

Puede sincronizar sus preferencias en varios equipos, crear y almacenar varios conjuntos de preferencias y compartirlas con compañeros de equipo. Puede instalar extensiones desde Visual Studio Marketplace, lo que le ofrece opciones adicionales para personalizar el comportamiento. Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Organizar el diseño de la ventana

Dentro de la ventana de Visual Studio, el espacio se divide en el menú principal, la barra de herramientas, el editor de código (o ventana de documento) y las ventanas de herramientas (como el Explorador de soluciones y la lista de errores). Algunas ventanas se superponen entre sí en la misma posición. Por ejemplo, el Explorador de soluciones, la vista de clases, la vista de recursos y el Explorador de Control de código fuente comparten la misma posición predeterminada. Puede cambiar entre ellos seleccionando las pestañas en la parte inferior del marco. Para hacer que dos o más de estas ventanas sean visibles al mismo tiempo, simplemente arrastre una de ellas por su barra de título a una nueva posición. Puede acoplarlo contra uno de los bordes de la ventana principal de Visual Studio, o puede flotarlo.

La siguiente captura de pantalla muestra la ventana de **Team Explorer** que se arrastra desde su posición predeterminada a una nueva posición acoplada en el lado izquierdo del editor de código. El área sombreada azul muestra dónde se colocará la ventana cuando se suelte el botón del ratón.

![Captura de pantalla de la ventana de Visual Studio Team Explorer, con el cambio de diseño resaltado](media/window-layout-move-team-explorer.png)

En la ventana del documento, cada archivo abierto está contenido en un marco con fichas. Puede flotar o bloquear estas pestañas, al igual que las ventanas de herramientas. Para obtener más información, vea [Personalizar diseños](/visualstudio/ide/customizing-window-layouts-in-visual-studio)de ventana en Visual Studio .

Para ocultar todas las ventanas de herramientas y maximizar la ventana Editor de código, pulse **Alt** + **Shift** + **Enter** para alternar el modo de *pantalla completa*.

## <a name="set-c-coding-styles-and-formatting"></a>Establecer estilos de codificación y formato C++

Puede especificar muchas opciones de formato de código individuales, como sangría y posiciones de llaves. Para ello, vaya **Tools** > a**Opciones** > de herramientas**Editor** > de**texto C/C++** > **Formato** (o escriba Ctrl **+ Q** y busque "Formato"). Como alternativa, puede especificar uno de los estilos [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (o su propio estilo ClangFormat personalizado).

![Captura de pantalla de las opciones de ClangFormat](media/clang-format-ide.png)

Para obtener más información sobre todas las opciones de formato, consulte Opciones, Editor de [texto, C/C++, Formato](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Establecimiento del tema de color

Para establecer un fondo claro u oscuro, escriba **Ctrl + Q** y busque "Tema de color". También puede encontrarlos en **Tools** > **Entorno**de**opciones** > de herramientas y seleccionando Tema **de color**.

![Captura de pantalla de temas de color](media/tools-options-color-theme.png)

Por ejemplo, este es el tema oscuro:

![Captura de pantalla de Visual Studio con tema de color oscuro](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Personalizar la coloración del código

En Visual Studio 2019, puede elegir entre tres esquemas de *color predefinidos.* Especifican cómo se colorean los elementos de código en el editor. Para elegir un tema, **Tools**vaya a > **Opciones** > de herramientas Editor > de**texto****C/C++** > **View**y elija Esquema de **color:**

![Captura de pantalla de las opciones de Esquema de color C++, con Mejorado resaltado](media/color-schemes.png)

En el esquema de color denominado **Visual Studio 2017**, la mayoría de los elementos de código son simplemente negros. En el esquema de color **mejorado,** se colorean las funciones, las variables locales, las macros y otros elementos. En el esquema **Mejorado (Globales frente a Miembros),** las funciones y variables globales se colorean para que contrasten con los miembros de la clase. El modo predeterminado es **Mejorado**y tiene este aspecto:

![Captura de pantalla del esquema de color mejorado](media/color-scheme-enhanced.png)

Independientemente del tema o esquema de color que esté activo, puede personalizar la fuente y los colores de los elementos de código individuales. **Environment** > Para ello, vaya a **Opciones** > **Options** > de herramientas**Fuentes y colores de** entorno (o escriba Ctrl + **Q** y busque "Fuentes"). Desplácese hacia abajo en la lista de elementos de visualización hasta que vea las opciones de C++.

![Captura de pantalla de las opciones de fuente y color de C++](media/tools-options-cpp-colors.png)

Los colores que se establecen aquí reemplazan los valores definidos para las esquemas de color. Si desea volver a los colores predeterminados para el esquema de color, establezca un color de nuevo en **Predeterminado**.

## <a name="customize-the-toolbars"></a>Personalizar las barras de herramientas

Las barras de herramientas proporcionan una manera cómoda de emitir comandos con un solo clic, en lugar de mediante los menús o métodos abreviados de teclado. Visual Studio incluye un conjunto estándar de barras de herramientas. Para el desarrollo estándar de C++, las barras de herramientas más útiles son probablemente Standard, Editor de texto, Compilar, Depurar, Control de código fuente y Comparar archivos. Para el desarrollo de Windows, el Editor de cuadros de diálogo y el Editor de imágenes son útiles para diseñar cuadros de diálogo y editar iconos.

Pase el cursor sobre los iconos de la barra de herramientas para ver qué comando representa:

![Captura de pantalla de iconos de la barra de herramientas, con un ejemplo de información de comandos disponible al mantener el mouse](media/toolbar-mouse-hover.png)

Puede agregar o quitar comandos, o crear una barra de herramientas personalizada, seleccionando la flecha abajo. Para mover la barra de herramientas a una nueva ubicación, arrástrela por la barra de puntos de la izquierda.

![Captura de pantalla de la barra de herramientas, con flecha abajo y barra punteada resaltada](media/toolbar-move-edit.png).

Para obtener más información, vea [Cómo: personalizar menús y barras](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio)de herramientas en Visual Studio .

## <a name="show-or-hide-line-numbers"></a>Mostrar u ocultar números de línea

Puede especificar si los números de línea se muestran a la izquierda de las ventanas del editor. En **Opciones**, en **C/C++**, seleccione **General**. En la sección **Configuración,** seleccione o desactive Números de **línea,** según sus preferencias.

![Captura de pantalla de las opciones generales, con los números de línea resaltados](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Crear atajos de teclado

Muchos comandos de Visual Studio tienen *métodos abreviados*de teclado, combinaciones de teclas con las teclas Ctrl, Alt y Mayús. Puede modificar estos métodos abreviados de teclado o crear otros nuevos propios en Visual Studio. Vaya **Tools** > a**Opciones** > de herramientas Teclado**de** **entorno** > (o escriba **Ctrl + Q** y busque "accesos directos"). Para obtener más información, vea [Identificar y personalizar métodos abreviados](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)de teclado en Visual Studio .
