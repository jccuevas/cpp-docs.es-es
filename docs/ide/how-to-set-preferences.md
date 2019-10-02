---
title: Establecer las C++ preferencias de código en Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816560"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Establecer las C++ preferencias de código en Visual Studio

Puede hacer que su C++ experiencia de codificación sea más cómoda, productiva y pleasurable mediante la personalización de Visual Studio. Puede realizar lo siguiente:

- Personalizar los menús y las barras de herramientas.
- Organice el diseño de la ventana.
- Establecer temas de color.
- Especifique C++ reglas de formato, incluidos varios estilos de ClangFormat.
- Crear métodos abreviados de teclado personalizados.

Puede sincronizar sus preferencias en varios equipos y crear y almacenar varios conjuntos de preferencias y compartirlos con compañeros de equipo. Puede instalar las extensiones desde el Visual Studio Marketplace, lo que le brinda opciones adicionales para personalizar el comportamiento. Para más información, vea [Personalizar el IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Organizar diseño de ventana

Dentro de la ventana de Visual Studio, el espacio se divide en el menú principal, la barra de herramientas, el editor de código (o la ventana de documento) y las ventanas de herramientas (como Explorador de soluciones y Lista de errores). Algunas ventanas se superponen entre sí en la misma posición. Por ejemplo, Explorador de soluciones, Vista de clases, Vista de recursos y Explorador de control de código fuente comparten la misma posición predeterminada. Para cambiar entre ellos, seleccione las pestañas en la parte inferior del marco. Para que dos o más de estas ventanas estén visibles al mismo tiempo, basta con arrastrar una de ellas por la barra de título hasta una nueva posición. Puede acoplarlo a uno de los bordes de la ventana principal de Visual Studio, o puede flotarlo.

En la captura de pantalla siguiente se muestra la **Team Explorer** ventana que se arrastra desde su posición predeterminada a una nueva posición acoplada en el lado izquierdo del editor de código. El área azul sombreado muestra dónde se colocará la ventana cuando se suelta el botón del mouse.

![Captura de pantalla de la ventana de Team Explorer de Visual Studio, con el cambio de diseño resaltado](media/window-layout-move-team-explorer.png)

En la ventana de documento, cada archivo abierto está contenido en un marco con pestañas. Puede flotar o bloquear estas pestañas, al igual que las ventanas de herramientas. Para obtener más información, vea [Personalizar los diseños de ventana de Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Para ocultar todas las ventanas de herramientas y maximizar la ventana del editor de código, presione **Alt** + **MAYÚS** + **entrar** para alternar el *modo de pantalla completa*.

## <a name="set-c-coding-styles-and-formatting"></a>Establecer C++ estilos y formato de codificación

Puede especificar muchas opciones de formato de código individuales, como la sangría y las posiciones de llaves. Para ello, vaya a **herramientas** > **Opciones** > **Editor de texto** > **C/C++**  > **formato** (o presione **Ctrl + Q** y busque "formato"). Como alternativa, puede especificar uno de los estilos [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (o su propio estilo personalizado de ClangFormat).

![Captura de pantalla de opciones de ClangFormat](media/clang-format-ide.png)

Para obtener más información sobre todas las opciones de formato, vea [Opciones, editor de textoC++, C/, formato](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Establecimiento del tema de color

Para establecer un fondo claro o oscuro, escriba **Ctrl + Q** y busque "tema de color". También puede encontrarlos si va a **herramientas** > **Opciones** > **entorno**y elige **tema de color**.

![Captura de pantalla de temas de color](media/tools-options-color-theme.png)

Por ejemplo, este es el tema oscuro:

![Captura de pantalla de Visual Studio con el tema de color oscuro](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Personalizar la coloración del código

En Visual Studio 2019, puede elegir entre tres *esquemas de colores*predefinidos. Estos especifican cómo se colorean los elementos de código en el editor. Para elegir un tema, vaya a **herramientas** > **Opciones** > **Editor de texto**@no__t-**5 CC++/**  > **vista**y elija **combinación de colores**:

![Captura de C++ pantalla de opciones de combinación de colores, con mejoras resaltadas](media/color-schemes.png)

En la combinación de colores denominada **Visual Studio 2017**, la mayoría de los elementos de código son simplemente negros. En la combinación de colores **mejorada** , se colorean las funciones, las variables locales, las macros y otros elementos. En el **Enhanced (Globals frente a Members) @no__t esquema-0, las funciones y las variables globales se colorean para contrastar a los miembros de clase. El modo predeterminado es **mejorado**y tiene el siguiente aspecto:

![Captura de pantalla de la combinación de colores mejorada](media/color-scheme-enhanced.png)

Independientemente del tema o la combinación de colores que esté activa, puede personalizar la fuente y los colores de los elementos de código individuales. Para ello, vaya a **herramientas** > **Opciones** > **entorno** > **fuentes y colores** (o presione **Ctrl + Q** y busque "fuentes"). Desplácese hacia abajo en la lista de elementos para mostrar C++ hasta ver las opciones.

![Captura de C++ pantalla de las opciones de fuente y color](media/tools-options-cpp-colors.png)

Los colores que establezca aquí invalidan los valores definidos para las combinaciones de colores. Si desea volver a los colores predeterminados para la combinación de colores, establezca un color de nuevo en **predeterminado**.

## <a name="customize-the-toolbars"></a>Personalizar las barras de herramientas

Las barras de herramientas proporcionan una manera cómoda de emitir comandos con un solo clic, en lugar de usar los menús o los métodos abreviados de teclado. Visual Studio incluye un conjunto estándar de barras de herramientas. Para el C++ desarrollo estándar, las barras de herramientas más útiles son probablemente estándar, editor de texto, compilar, depurar, control de código fuente y comparar archivos. Para el desarrollo de Windows, el editor de cuadros de diálogo y el editor de imágenes son útiles para diseñar cuadros de diálogo y iconos de edición.

Mantenga el mouse sobre los iconos de la barra de herramientas para ver qué comando representa:

![Captura de pantalla de los iconos de barra de herramientas, con un ejemplo de información de comandos disponible al mantener el mouse](media/toolbar-mouse-hover.png)

Puede Agregar o quitar comandos, o crear una barra de herramientas personalizada; para ello, seleccione la flecha hacia abajo. Para desplace la barra de herramientas a una nueva ubicación, arrástrela por la barra de puntos de la izquierda.

![Captura de pantalla de la barra de herramientas, con la flecha hacia abajo y la barra de puntos resaltada](media/toolbar-move-edit.png).

Para obtener más información, vea [Cómo: Personalización de menús y barras de herramientas en Visual Studio @ no__t-0.

## <a name="show-or-hide-line-numbers"></a>Mostrar u ocultar números de línea

Puede especificar si los números de línea se muestran a la izquierda de las ventanas del editor. En **Opciones**, en **C/C++** , seleccione **General**. En la sección **configuración** , seleccione o borre **los números de línea**, en función de sus preferencias.

![Captura de pantalla de las opciones generales, con los números de línea resaltados](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Crear métodos abreviados de teclado

Muchos comandos de Visual Studio disponen de *métodos abreviados de teclado*, combinaciones de teclas con las teclas Ctrl, Alt y Mayús. Puede modificar estos métodos abreviados de teclado o crear unos nuevos en Visual Studio. Vaya a **herramientas** > **Opciones** > **entorno** > **Keyboard** (o presione **Ctrl + Q** y busque "accesos directos"). Para obtener más información, vea [identificar y personalizar métodos abreviados de teclado en Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
