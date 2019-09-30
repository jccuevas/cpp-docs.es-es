---
title: Establecer las C++ preferencias de código en Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, menus and more in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 90c9f39135b90a2c5015861a78dd8760b9a8aeed
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686951"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Establecer las C++ preferencias de código en Visual Studio

Puede hacer que su C++ experiencia de codificación sea más cómoda, productiva y pleasurable mediante la personalización de Visual Studio. Puede personalizar los menús y las barras de herramientas, organizar el diseño de la ventana, establecer temas C++ de color, especificar reglas de formato, incluidas varias versiones de ClangFormat, y crear métodos abreviados de teclado personalizados. Puede sincronizar sus preferencias en varios equipos y crear y almacenar varios conjuntos de preferencias y compartirlos con compañeros de equipo. Puede instalar las extensiones desde el Visual Studio Marketplace que proporcionan un comportamiento personalizado adicional. Muchas de estas opciones se documentan en [Personalización del IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Organizar diseño de ventana

Dentro de la ventana de Visual Studio, el espacio se divide en el menú principal, en la barra de herramientas, en el editor de código (o ventana de documento) y en las ventanas de herramientas (**Explorador de soluciones**, **lista de errores**, etc.). Algunas ventanas se superponen entre sí en la misma posición. Por ejemplo, **Explorador de soluciones**, **vista de clases**, **vista de recursos**y **Explorador de control de código fuente** comparten la misma posición predeterminada. Para cambiar entre ellas, haga clic en las pestañas de la parte inferior del marco. Para que dos o más de estas ventanas estén visibles al mismo tiempo, basta con arrastrar una de ellas por la barra de título hasta una nueva posición. Puede acoplarlo a uno de los bordes de la ventana principal de Visual Studio, o puede flotarlo. En la ilustración siguiente se muestra la **Team Explorer** ventana en el proceso de arrastrar desde su posición predeterminada a una nueva posición acoplada en el lado izquierdo del editor de código. El área azul sombreado muestra dónde se colocará la ventana cuando se suelta el botón del mouse.

![Modificar el diseño de la ventana](media/window-layout-move-team-explorer.png)

En la ventana de documento, cada archivo abierto está contenido en un marco con pestañas. Puede flotar o bloquear estas pestañas, al igual que las ventanas de herramientas. Para obtener más información, vea [Personalizar los diseños de ventana de Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Para ocultar todas las ventanas de herramientas y maximizar la ventana del editor de código, presione **Alt** + **MAYÚS** + **entrar** para alternar el *modo de pantalla completa*.

## <a name="set-c-coding-styles-and-formatting"></a>Establecer C++ estilos y formato de codificación

Puede especificar muchas opciones de formato de código individuales, como la sangría y las posiciones de llaves, navegando a **herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **formato** (o tipo **Ctrl + Q** y busque "formato"). Como alternativa, puede especificar uno de los estilos [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (o su propio estilo personalizado de ClangFormat):

![Opciones de ClangFormat](media/clang-format-ide.png)

Para obtener más información sobre todas las opciones de formato, vea [Opciones, editor de textoC++, C/, formato](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Establecimiento del tema de color

Para establecer un fondo claro o oscuro, escriba **Ctrl + Q** y busque "tema de color". También puede obtenerla a través de las **herramientas** > **Opciones**@no__t **-3 y** elegir **tema de color**:

![Temas de color](media/tools-options-color-theme.png)

En la imagen siguiente se muestra el tema oscuro:

![Tema oscuro](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Personalizar la coloración del código

En Visual Studio 2019 puede elegir entre tres *esquemas de color* predefinidos que especifican cómo se colorean los elementos de código en el editor. Para elegir un tema, vaya a **herramientas** > **Opciones** > **Editor de texto**@no__t-**5 CC++/**  > **Ver** y elija **combinación de colores**:

![C++Combinaciones de colores](media/color-schemes.png)

En la combinación de colores de **Visual Studio 2017** , la mayoría de los elementos de código son simplemente negros. En la combinación de colores **mejorada** , se colorean las funciones, las variables locales, las macros y otros elementos. En el **Enhanced (Globals frente a Members) @no__t esquema-0, las funciones y las variables globales se colorean para contrastar a los miembros de clase. El modo predeterminado es **mejorado** y tiene el siguiente aspecto:

![Combinación de colores mejorada](media/color-scheme-enhanced.png)

Independientemente del tema o la combinación de colores que esté activa, puede personalizar la fuente y los colores de los elementos de código individuales Si navega a **herramientas** > **Opciones** > **entorno** > **fuentes y colores** (o tipo  **Ctrl + Q** y busque "fuentes"). Desplácese hacia abajo en la lista de elementos para mostrar C++ hasta que vea las opciones:

![C++Opciones de fuente y color](media/tools-options-cpp-colors.png)

Los colores que establezca aquí invalidan los valores definidos para las combinaciones de colores. Debe volver a establecer un color como **predeterminado** si lo ha cambiado pero desea usar los colores predeterminados para la combinación de colores.

## <a name="customize-the-toolbars"></a>Personalizar las barras de herramientas

Las barras de herramientas proporcionan una manera cómoda de emitir comandos con un solo clic del mouse, en lugar de usar los menús o los métodos abreviados de teclado. Visual Studio incluye un conjunto estándar de barras de herramientas. Para el C++ desarrollo estándar, las barras de herramientas más útiles son probablemente estándar, editor de texto, compilación, depuración, control de código fuente y posiblemente comparen archivos. Para el desarrollo de Windows, el editor de cuadros de diálogo y el editor de imágenes son útiles para diseñar cuadros de diálogo y editar iconos.

Mantenga el mouse sobre los iconos de la barra de herramientas para ver qué comando representa:

![Barra de herramientas QuickInfo](media/toolbar-mouse-hover.png)

Para agregar o quitar comandos o para crear una barra de herramientas personalizada, haga clic en la flecha hacia abajo. Para desplace la barra de herramientas a una nueva ubicación, arrástrela por la barra de puntos de la izquierda:

![Personalizar o desplace una barra de herramientas](media/toolbar-move-edit.png).

Para obtener más información, vea [Cómo: Personalización de menús y barras de herramientas en Visual Studio @ no__t-0.

## <a name="show-or-hide-line-numbers"></a>Mostrar u ocultar números de línea

Para especificar si los números de línea se muestran a la izquierda de las ventanas del editor, desplácese a y compruebe o anule la comprobación de **los números de línea**:

![Números de línea](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Crear métodos abreviados de teclado

Todos los comandos de Visual Studio se pueden realizar con métodos abreviados de teclado usando varias combinaciones de teclas con las teclas Ctrl, Alt y Mayús. Puede crear sus propios accesos directos navegando a **herramientas** > **Opciones** > **entorno**@no__t **-5 (** o presione **Ctrl + Q** y busque "accesos directos"). Para obtener más información, vea [identificar y personalizar métodos abreviados de teclado en Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
