---
title: Optimización guiada por perfiles del concentrador Rendimiento y diagnósticos
ms.date: 03/14/2018
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
ms.openlocfilehash: 57e0c32b401f2c1c3216a120bc86efa649ee0104
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580861"
---
# <a name="profile-guided-optimization-in-the-visual-studio-2013-performance-and-diagnostics-hub"></a>En el concentrador de diagnósticos y rendimiento de Visual Studio 2013 la optimización guiada por perfiles

Si usa Visual Studio 2013, la optimización guiada por perfiles para Visual C++ de complemento en el Hub rendimiento y diagnósticos simplifica la experiencia de optimización guiada por perfiles para los desarrolladores. También puede [descargar el complemento](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC) desde el sitio Web de Visual Studio. El complemento no se admite en versiones posteriores de Visual Studio.

La optimización guiada por perfiles (PGO) ayuda a crear compilaciones de aplicaciones nativas x86 y x64 optimizadas para la forma en que los usuarios interactúan con ellas. PGO es un proceso de varios pasos: crear una compilación de la aplicación que se ha instrumentado para generación de perfiles y, a continuación, realizar "aprendizaje". Es decir, se ejecuta la aplicación instrumentada a través de escenarios comunes de interacción de usuario. Los datos de generación de perfiles capturados se guardan y después la aplicación se recompila, usando los resultados para orientar la optimización de todo el programa. Si bien estos pasos pueden realizarse individualmente en Visual Studio o en la línea de comandos, el complemento PGO centraliza y simplifica el proceso. El complemento PGO establece todas las opciones necesarias, le guía a través de cada paso, presenta el análisis obtenido y, a continuación, usa los resultados para configurar la compilación de forma que se optimice el tamaño o la velocidad de cada función. Además, dicho complemento facilita volver a ejecutar la formación de la aplicación y actualizar los datos de optimización de la compilación cuando cambia el código.

## <a name="prerequisites"></a>Requisitos previos

Debe [descargar el complemento PGO](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC) e instalarlo en Visual Studio antes de usarlo en el Hub rendimiento y diagnósticos.

## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>Tutorial: usar el complemento PGO para optimizar una aplicación

En primer lugar, se creará una aplicación de escritorio de Win32 básica en Visual Studio. Si ya tiene una aplicación nativa que desea optimizar, puede usarla y omitir este paso.

### <a name="to-create-an-app"></a>Para crear una aplicación

1. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.

1. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda **instalado**, **plantillas**, **Visual C++** y, a continuación, seleccione  **MFC**.

1. En el panel central, seleccione **aplicación MFC**.

1. Especifique un nombre para el proyecto, por ejemplo, **SamplePGOProject**: en el **nombre** cuadro. Elija el botón **Aceptar** .

1. En el **Introducción** página de la **MFC Application Wizard** cuadro de diálogo, seleccione el **finalizar** botón.

A continuación, establezca la configuración de compilación de la aplicación en Lanzamiento para prepararla para los pasos de compilación y aprendizaje de PGO.

### <a name="to-set-the-build-configuration"></a>Para establecer la configuración de compilación

1. En la barra de menús, elija **Compilar**, **Administrador de configuración**.

1. En el **Configuration Manager** diálogo cuadro, elija el **configuración de soluciones activas** botón desplegable y seleccione **versión**. Elija la **cerrar** botón.

Abra el concentrador rendimiento y diagnósticos, en la barra de menús, elija **analizar**, **rendimiento y diagnósticos**. Esto abre una página de la sesión de diagnósticos con las herramientas de análisis disponibles para el tipo de proyecto.

![PGO en el Hub rendimiento y diagnósticos](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")

En **herramientas disponibles**, seleccione el **optimización guiada por perfiles** casilla de verificación. Elija la **iniciar** botón para iniciar el complemento PGO.

![Página de introducción de PGO](../../build/reference/media/pgofig1start.png "PGOFig1Start")

El **optimización guiada por perfiles** página describen los pasos que el complemento usa para mejorar el rendimiento de la aplicación. Elija la **iniciar** botón.

![Página de instrumentación de PGO](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")

En el **instrumentación** sección, usa el **aprendizaje se habilita inicialmente** posibilidad de elegir si se debe incluir la fase de inicio de la aplicación como parte de la formación. Si no se selecciona esta opción, los datos de aprendizaje no se registran en una aplicación instrumentada en ejecución hasta que no se habilite explícitamente el aprendizaje.

Elija la **instrumento** botón para compilar la aplicación con un conjunto especial de opciones del compilador. El compilador inserta instrucciones de sondeo en el código generado. Estas instrucciones registran los datos de generación de perfiles durante la fase de aprendizaje.

![Página compilación instrumentada de PGO](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")

Cuando la compilación instrumentada de la aplicación se completa, la aplicación se inicia automáticamente.

Si hay errores o advertencias se producen durante la compilación, corríjalos y, a continuación, elija **reiniciar compilación** para reiniciar la compilación instrumentada.

Cuando se inicia la aplicación, puede usar el **iniciar aprendizaje** y **pausar aprendizaje** vínculos en el **entrenamiento** sección para controlar cuándo se registra la información de generación de perfiles. Puede usar el **detener aplicación** y **Iniciar aplicación** vínculos para detener y reiniciar la aplicación.

![Página de aprendizaje de PGO](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")

Durante la formación, recorra los escenarios de usuario para capturar la información de generación de perfiles que el complemento PGO necesita para optimizar el código. Cuando haya completado el aprendizaje, cierre la aplicación o elija el **detener aplicación** vínculo. Elija la **analizar** botón para iniciar el paso de análisis.

Cuando se completa, el análisis del **Analysis** sección muestra un informe de la información de generación de perfiles que se capturaron durante la fase de aprendizaje del escenario de usuario. Puede usar este informe para examinar las funciones a las que más llamó la aplicación y a las que dedicó más tiempo. El complemento PGO usa la información para determinar en qué funciones de la aplicación se va a optimizar la velocidad y en cuáles el tamaño. El complemento PGO configura optimizaciones de compilación a fin de crear la aplicación más pequeña y rápida para los escenarios de usuario registrados durante el aprendizaje.

![Página de análisis de PGO](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")

Si el aprendizaje capturó la información de generación de perfiles esperada, puede elegir **guardar cambios** para guardar los datos de perfil analizados en el proyecto para optimizar futuras compilaciones. Para descartar los datos de perfil y comenzar el aprendizaje sobre desde el principio, elija **rehacer el aprendizaje**.

El archivo de datos de perfil se guarda en el proyecto en un **datos de entrenamiento de PGO** carpeta. Estos datos se usan para controlar la configuración de optimización de compilación del compilador en la aplicación.

![Archivo de datos PGO en el Explorador de soluciones](../../build/reference/media/pgofig6data.png "PGOFig6Data")

Después del análisis, el complemento PGO establece opciones de compilación en el proyecto para usar los datos de perfil para optimizar selectivamente la aplicación durante la compilación. Puede seguir modificando y compilando la aplicación con los mismos datos de perfil. Cuando se compila la aplicación, los resultados de la compilación notifican cuántas funciones e instrucciones se optimizaron usando los datos de perfil.

![Diagnósticos de salida de PGO](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")

Si realiza cambios de código significativos durante el desarrollo, es posible que tenga que volver a aplicar el entrenamiento a la aplicación para obtener las mejores optimizaciones. Se recomienda volver a aplicar el entrenamiento a la aplicación cuando los resultados de la compilación notifican que menos del 80 % de las funciones o instrucciones se optimizaron usando los datos de perfil.