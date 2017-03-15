---
title: "Usar compatibilidad nativa con múltiples versiones para compilar proyectos antiguos en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8953e3bd81158ce183e1abb5dfa969164c1f9ced
ms.openlocfilehash: 1088f17c1d758589fba146f82b2544ae17090a22
ms.lasthandoff: 02/24/2017

---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Usar compatibilidad nativa con múltiples versiones para compilar proyectos antiguos en Visual Studio  
  
Normalmente se recomienda actualizar los proyectos al instalar la versión más reciente de Visual Studio. El costo de actualización de los proyectos y el código normalmente se ve compensado por las ventajas del IDE nuevo, el compilador, las bibliotecas y las herramientas. Pero se sabe que a veces no se pueden actualizar algunos proyectos. Puede haber archivos binarios que están vinculados a plataformas o bibliotecas más antiguas que por motivos de mantenimiento no se puedan actualizar. El código podría usar construcciones de lenguaje no estándar que se romperían al migrar a un compilador más reciente. El código podría depender de bibliotecas de terceros compiladas para una versión concreta de Visual C++. O bien podría generar bibliotecas para otros usuarios para una versión anterior concreta de Visual C++.  
  
Afortunadamente, puede usar Visual Studio 2017 y Visual Studio 2015 para compilar proyectos para conjuntos de herramientas de compilador y bibliotecas anteriores. No tiene que actualizar un proyecto de Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 o Visual Studio 2015 para aprovechar las nuevas características del IDE:  
 - Nuevas capacidades de refactorización de C++ y características experimentales de editor  
 - Nuevas ventanas de herramientas de diagnóstico del depurador y lista de errores  
 - Puntos de interrupción renovados, ventana de excepciones y nuevas sugerencias de rendimiento  
 - Nuevas herramientas de navegación por el código y búsqueda  
 - Nuevas revisiones rápidas de C++ y extensiones de herramientas de productividad avanzadas.  
  
También puede compilar para proyectos de Visual Studio 2008, pero no se pueden usar sin cambios. Para más información, vea las instrucciones de la sección Visual Studio 2008.
  
Las versiones más recientes de Visual Studio admiten la compatibilidad nativa con múltiples versiones y los recorridos de ida y vuelta de proyectos. La compatibilidad nativa con múltiples versiones es la capacidad del IDE más reciente de compilar mediante conjuntos de herramientas instalados por versiones anteriores de Visual Studio. El recorrido de ida y vuelta es la capacidad del IDE más reciente de cargar proyectos creados con una versión anterior del IDE sin realizar cambios en el proyecto. Si instala la versión más reciente de Visual Studio en paralelo con la versión existente, puede usar la nueva versión del IDE con el compilador y las herramientas de la versión existente para compilar los proyectos. Otros miembros del equipo pueden seguir usando los proyectos en la versión anterior de Visual Studio.  
  
Al usar un conjunto de herramientas anterior, puede aprovechar muchas de las características más recientes del IDE, pero no los avances más recientes en el compilador de C++, las bibliotecas ni las herramientas de compilación. Por ejemplo, no podrá usar las nuevas mejoras de conformidad de lenguaje, las nuevas características de depuración y análisis de código ni aprovechar el rendimiento de compilación más rápido del conjunto de herramientas más reciente. También hay algunas características del IDE que no son compatibles con conjuntos de herramientas anteriores. Por ejemplo, puede faltar información de tipos en el generador de perfiles de memoria y la operación de refactorización "Convertir en literales de cadena sin formato" genera código compatible con C ++11 que no se compilará al usar Visual Studio 2012 o conjuntos de herramientas anteriores.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Cómo usar la compatibilidad nativa con múltiples versiones en Visual Studio
Una vez que haya instalado Visual Studio en paralelo con la versión anterior, abra el proyecto existente en la nueva versión de Visual Studio. Cuando se cargue el proyecto, Visual Studio le preguntará si quiere actualizarlo para usar el compilador de C++ y las bibliotecas más recientes. Dado que quiere que el proyecto conserve el compilador y las bibliotecas anteriores, elija el botón **Cancelar**.  
  
Visual Studio insiste en actualizar el proyecto. Para evitar que aparezca el cuadro de diálogo de actualización cada vez que carga el proyecto, puede definir la siguiente propiedad en los proyectos o en los archivos .props y .targets que importan:  
  
`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`  
  
Debe quitar esta propiedad cuando quiera actualizar los proyectos.  
  
Si decide no actualizar, Visual Studio no realiza ningún cambio en los archivos de solución o proyecto. Al compilar el proyecto, los archivos binarios generados son totalmente compatibles con los compilados con la versión anterior de Visual Studio. Esto es porque Visual Studio usa el mismo compilador de C++ y vincula las mismas bibliotecas incluidas en el IDE anterior. Esa es la razón por la que el cuadro de diálogo de actualización le advierte de que mantenga la versión anterior de Visual Studio instalada si elige **Cancelar**.  
  
## <a name="instructions-for-visual-studio-2008"></a>Instrucciones para Visual Studio 2008  
  
Visual Studio 2008 tenía su propio sistema de compilación dedicado para C++ denominado VCBuild. A partir de Visual Studio 2010, los proyectos de Visual C++ se cambiaron para usar MSBuild. Esto significa que debe seguir un paso de actualización para compilar los proyectos de Visual Studio 2008 en la versión más reciente de Visual Studio. El proyecto actualizado todavía genera archivos binarios que son totalmente compatibles con los creados mediante el IDE de Visual Studio 2008.

En primer lugar, además de la versión actual de Visual Studio, debe instalar Visual Studio 2010 en el mismo equipo que Visual Studio 2008. Solo Visual Studio 2010 instala los scripts de MSBuild necesarios para los proyectos de Visual Studio 2008. 

A continuación, debe actualizar los proyectos y la solución de Visual Studio 2008 a la versión actual de Visual Studio. Se recomienda crear una copia de seguridad de los proyectos y los archivos de solución antes de la actualización. Para iniciar el proceso de actualización, abra la solución en la versión actual de Visual Studio. Cuando aparezca el mensaje de actualización, revise la información mostrada y luego elija **Aceptar** para iniciar la actualización. Si tiene más de un proyecto en la solución, debe actualizar el asistente para crear nuevos archivos de proyecto .vcxproj en paralelo con los archivos .vcproj existentes. Siempre que además tenga una copia del archivo .sln original, la actualización no tiene ningún impacto en los proyectos existentes de Visual Studio 2008.

Una vez finalizada la actualización, si el informe de registro tiene errores o advertencias sobre cualquiera de los proyectos, examínelos detenidamente. La conversión de VCBuild a MSBuild puede causar problemas. Asegúrese de comprender e implementar los elementos de acción que aparecen en el informe. Para más información sobre el informe de registro de actualización y los problemas que pueden surgir al convertir VCBuild en MSBuild, vea esta entrada de blog [C++ Native Multi-Targeting](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) (Compatibilidad nativa con múltiples versiones de C++).

Una vez completada la actualización del proyecto y corregidos los problemas que aparezcan en el archivo de registro, la solución ya tiene realmente como destino el conjunto de herramientas más reciente. Como paso final, cambie las propiedades de cada proyecto de la solución para usar el conjunto de herramientas de Visual Studio 2008. Con la solución cargada en la versión actual de Visual Studio, para cada proyecto de la solución, abra el cuadro de diálogo **Páginas de propiedades**: haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y luego seleccione **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, cambie el valor de la lista desplegable **Configuración** a **Todas las configuraciones**. En **Propiedades de configuración**, seleccione **General** y después cambie **Conjunto de herramientas de la plataforma** a **Visual Studio 2008 (v90)**.  
  
Después de este cambio, se usan el compilador y las bibliotecas de Visual Studio 2008 para generar archivos binarios de proyecto al compilar la solución en la versión actual de Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Instalar un conjunto de herramientas de Visual Studio anterior  
  
Puede que tenga un proyecto de Visual C++ anterior que no pueda o no quiera actualizar, pero no la versión del conjunto de herramientas de la plataforma que coincide con el proyecto. En este caso, para obtener el conjunto de herramientas, puede instalar la edición gratuita Visual Studio Community o Express de la versión que necesita. Cada versión de Visual Studio a partir de Visual Studio 2008 puede instalar el compilador, las herramientas y las bibliotecas que necesita para esa versión de Visual Studio actual. Busque en el Centro de descarga de Microsoft y descargue una versión determinada de Visual Studio. Asegúrese de elegir las opciones de instalación de C++ durante la instalación. Una vez completada la instalación, ejecute esa versión de Visual Studio para instalar las actualizaciones. Busque también los cambios de Windows Update que pueda necesitar. Es posible que haya que repetir este proceso de comprobación de actualización más de una vez para obtener todas las actualizaciones.  
  
Estas son algunas de las descargas de Visual Studio que puede necesitar:  
  
  - [Microsoft Visual Studio Community 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48146)  
  - [Microsoft Visual Studio Express 2013 para escritorio de Windows con Update 5](https://www.microsoft.com/en-us/download/details.aspx?id=48131)  
  - [Microsoft Visual Studio Express 2012 para escritorio de Windows](https://www.microsoft.com/en-us/download/details.aspx?id=34673)  
  - [Visual Studio 2012 Update 5](https://www.microsoft.com/en-us/download/details.aspx?id=34673)  
  - [Microsoft Visual C++ 2010 Express (instalador web)](https://download.microsoft.com/download/1/D/9/1D9A6C0E-FC89-43EE-9658-B9F0E3A76983/vc_web.exe)  
  - [Microsoft Visual Studio 2010 Service Pack 1](https://www.microsoft.com/en-us/download/details.aspx?id=23691)  
  - [Microsoft Visual C++ 2008 Express con SP1 (instalador web)](https://go.microsoft.com/?linkid=7729279)  
  
Con estos productos instalados, 
  
## <a name="see-also"></a>Vea también  
 [Actualizar proyectos desde versiones anteriores de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 [Mejoras de conformidad de C++ en Visual Studio 2017](../cpp-conformance-improvements-2017.md)  

