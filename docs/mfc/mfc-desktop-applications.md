---
title: Aplicaciones de escritorio de MFC
ms.date: 07/28/2019
f1_keywords:
- MFC
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: e9921d18e9ec060f61959278b68906338f02b5b7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447710"
---
# <a name="mfc-desktop-applications"></a>Aplicaciones de escritorio de MFC

La biblioteca de Microsoft Foundation Class (MFC) proporciona un contenedor orientado a objetos en gran parte de las API de Win32 y de COM. Aunque se puede usar para crear aplicaciones de escritorio muy simples, es muy útil cuando se necesita desarrollar interfaces de usuario más complejas con varios controles. Puede usar MFC para crear aplicaciones con interfaces de usuario de estilo Office. Para obtener documentación sobre la propia plataforma Windows, consulte la [documentación de Windows](/windows/index). Para obtener información sobre cómo compilar aplicaciones de Windows en sin MFC, vea C++ [compilar aplicaciones de Windows de escritorio mediante la API de Win32](/windows/win32/index).

La referencia de MFC incluye las clases, las funciones globales, las variables globales y las macros que constituyen la biblioteca MFC (Microsoft Foundation Class).

Los gráficos individuales de jerarquía que se incluyen con cada clase son útiles para buscar clases base. La referencia de MFC no describe normalmente funciones de miembro heredadas ni operadores heredados. Para obtener información acerca de estas funciones, haga referencia a las clases base descritas en los diagramas de jerarquía.

La documentación de cada clase incluye información general sobre la clase, un resumen del miembro por categoría y temas para las funciones miembro, los operadores sobrecargados y los miembros de datos.

Los miembros de clase públicos y protegidos se documentan solo cuando se utilizan normalmente en programas de aplicación o clases derivadas. Vea los archivos de encabezado de clase para obtener una lista completa de miembros de clase.

> [!IMPORTANT]
>  Las clases MFC y sus miembros no se pueden usar en aplicaciones que se ejecutan en el entorno de Windows Runtime.
>
>  Las bibliotecas MFC (DLL) para la codificación de caracteres multibyte (MBCS) ya no se incluyen en Visual Studio, pero están disponibles como complemento de Visual Studio. Para obtener más información, vea [complemento dll de MBCS para MFC](mfc-mbcs-dll-add-on.md).

## <a name="in-this-section"></a>En esta sección

[Conceptos](mfc-concepts.md)<br/>
Artículos conceptuales sobre temas de MFC.

[Gráfico de jerarquías](hierarchy-chart.md)<br/>
Detalla visualmente las relaciones entre clases en la biblioteca de clases.

[Información general sobre clases](class-library-overview.md)<br/>
Muestra las clases de la biblioteca MFC por categorías.

[Tutoriales](walkthroughs-mfc.md)<br/>
Contiene artículos que le guiarán por diversas tareas asociadas a las características de la biblioteca MFC.

[Notas técnicas](mfc-technical-notes.md)<br/>
Proporciona vínculos a temas especializados, escritos por el equipo de desarrollo de MFC, en la biblioteca de clases.

[Personalización de MFC](customization-for-mfc.md)<br/>
Proporciona algunas sugerencias para personalizar la aplicación MFC.

[Clases](reference/mfc-classes.md)<br/>
Proporciona vínculos e información de archivo de encabezado para las clases MFC.

[Clases internas](reference/internal-classes.md)<br/>
Se utiliza de forma interna en MFC. Por integridad, en esta sección se describen estas clases internas, pero no están destinadas a usarse directamente en el código.

[Macros y variables globales](reference/mfc-macros-and-globals.md)<br/>
Proporciona vínculos a las macros y funciones globales en la biblioteca MFC.

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Proporciona vínculos a las estructuras, los estilos, las devoluciones de llamada y los mapas de mensajes utilizados por la biblioteca MFC.

[Asistentes y cuadros de diálogo de MFC](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Guía sobre las características de Visual Studio para crear aplicaciones MFC.

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
Cómo usar archivos de recursos para administrar datos de la interfaz de usuario (IU) estáticos, como las cadenas de la IU y el diseño de los cuadros de diálogo.

## <a name="related-sections"></a>Secciones relacionadas

[Categorías de gráfico de jerarquías](hierarchy-chart-categories.md)<br/>
Describe el gráfico de jerarquías de MFC por categoría.

[Clases compartidas de ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Proporciona vínculos a las clases que se comparten entre MFC y ATL.

[Ejemplos de MFC](../overview/visual-cpp-samples.md)<br/>
Proporciona vínculos a ejemplos que muestran cómo utilizar MFC.

[Referencia de bibliotecas de Visual C++](../standard-library/cpp-standard-library-reference.md)<br/>
Proporciona vínculos a las diversas bibliotecas suministradas con Visual C++, incluidas las bibliotecas de ATL, MFC, las plantillas OLE DB, la biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++.

[Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Proporciona vínculos sobre cómo utilizar el depurador de Visual Studio para corregir errores lógicos en sus aplicaciones o procedimientos almacenados.

## <a name="see-also"></a>Consulte también

[MFC y ATL](mfc-and-atl.md)
