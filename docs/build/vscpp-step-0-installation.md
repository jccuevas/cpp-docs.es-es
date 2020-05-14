---
title: Instalación de compatibilidad con C++ en Visual Studio
description: Instalación de la compatibilidad de Visual Studio con Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: d3018bef9254a8eab557057c035cde84310a2452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335364"
---
# <a name="install-c-support-in-visual-studio"></a>Instalación de compatibilidad con C++ en Visual Studio

Si aún no se ha descargado e instalado Visual Studio C++ y las herramientas de Visual C++, aquí se muestra cómo empezar a trabajar.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Instalación de Visual Studio 2019

Bienvenido a Visual Studio 2019. En esta versión, resulta muy fácil elegir e instalar solo las características que se necesitan. Además, gracias a la mínima superficie de memoria que ocupa, se instala rápidamente y con menos impacto en el sistema.

> [!NOTE]
> Este tema se aplica a la instalación de Visual Studio en Windows. [Visual Studio Code](https://code.visualstudio.com/) es un entorno de desarrollo ligero y multiplataforma que se ejecuta en sistemas Windows, Mac y Linux. La extensión Microsoft [C/C++ para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) admite IntelliSense, depuración, formato de código y finalización automática. Visual Studio para Mac no es compatible con Microsoft C++, pero admite lenguajes .NET y desarrollo multiplataforma. Para obtener instrucciones de instalación, vea [Instalación de Visual Studio para Mac](/visualstudio/mac/installation/).

¿Quiere saber más sobre otras novedades de esta versión? Vea las [notas de la versión](/visualstudio/releases/2019/release-notes/) de Visual Studio.

¿Está listo para instalarlo? Le guiaremos paso a paso.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Paso 1: Asegurarse de que el equipo está listo para Visual Studio

Antes de comenzar la instalación de Visual Studio:

1. Compruebe los [requisitos del sistema](/visualstudio/releases/2019/system-requirements). Estos requisitos le permiten saber si el equipo es compatible con Visual Studio 2019.

1. Aplique las actualizaciones de Windows más recientes. Estas actualizaciones garantizan que el equipo tiene las actualizaciones de seguridad más recientes y los componentes del sistema necesarios para Visual Studio.

1. Reinicie el equipo. El reinicio garantiza que cualquier actualización o instalación pendiente no dificultará la instalación de Visual Studio.

1. Libere espacio. Quite los archivos y aplicaciones innecesarios de %SystemDrive% ejecutando, por ejemplo, la aplicación Liberar espacio.

Si tiene dudas sobre cómo ejecutar versiones anteriores de Visual Studio en paralelo con Visual Studio 2019, vea la página [Compatibilidad y destinatarios de la plataforma de Visual Studio 2019](/visualstudio/releases/2019/compatibility/).

### <a name="step-2---download-visual-studio"></a>Paso2: Descargar Visual Studio

A continuación, descargue el archivo de programa previo de Visual Studio. Para ello, elija el siguiente botón, la edición de Visual Studio que quiera instalar, **Guardar** y, por último, **Abrir carpeta**.

 > [!div class="button"]
 > [Descarga de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Paso 3: Instalar el Instalador de Visual Studio

Ejecute el archivo de programa previo para instalar el Instalador de Visual Studio. Este nuevo instalador ligero incluye todo lo necesario para instalar y personalizar Visual Studio.

1. Desde la carpeta **Descargas**, haga doble clic en el archivo de programa previo que coincida o sea similar a uno de los siguientes archivos:

   - **vs_community.exe** para Visual Studio Community
   - **vs_professional.exe** para Visual Studio Professional
   - **vs_enterprise.exe** para Visual Studio Enterprise

   Si recibe un aviso de Control de cuentas de usuario, elija **Sí**.

1. Le pediremos que acepte los [Términos de licencia](https://visualstudio.microsoft.com/license-terms/) de Microsoft y la [Declaración de privacidad](https://privacy.microsoft.com/privacystatement) de Microsoft. Elija **Continuar**.

### <a name="step-4---choose-workloads"></a>Paso 4: Elegir las cargas de trabajo

Una vez instalado el Instalador, puede usarlo para personalizar la instalación mediante la selección de las *cargas de trabajo* o los conjuntos de características que quiera. Esta es la manera de hacerlo.

1. Busque la carga de trabajo que quiera en la pantalla **Instalando Visual Studio**.

   ![Visual Studio 2019: Instalación de una carga de trabajo](../get-started/media/vs-installer-workloads.png)

   Para obtener compatibilidad principal con C++, elija la carga de trabajo "Desarrollo para el escritorio con C++". Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.

   Las cargas de trabajo adicionales admiten otros tipos de desarrollo de C++. Por ejemplo, elija la carga de trabajo "Desarrollo de la Plataforma universal de Windows" para crear aplicaciones que usen Windows Runtime para Microsoft Store. Elija "Desarrollo de juegos con C++" para crear juegos que usen DirectX, Unreal y Cocos2d. Elija "Desarrollo para Linux con C++" para establecer como destino las plataformas Linux, incluido el desarrollo para IoT.

   En el panel **Detalles de la instalación** se enumeran los componentes incluidos y opcionales que ha instalado cada carga de trabajo. Se pueden seleccionar o anular la selección de los componentes opcionales de esta lista. Por ejemplo, para admitir el desarrollo mediante los conjuntos de herramientas de compilador de Visual Studio 2017 o 2015, elija los componentes opcionales MSVC v141 o MSVC v140. Se puede agregar compatibilidad con MFC, la extensión de lenguaje de los módulos experimentales, IncrediBuild y mucho más.

1. Después de elegir las cargas de trabajo y los componentes opcionales que quiera, elija **Instalar**.

   Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

> [!TIP]
> En cualquier momento después de la instalación, puede instalar las cargas de trabajo o los componentes que no instaló inicialmente. Si tiene Visual Studio abierto, vaya a **Herramientas** > **Obtener herramientas y características...** para abrir el Instalador de Visual Studio. O bien, abra el **Instalador de Visual Studio** desde el menú Inicio. A partir de ahí, puede elegir las cargas de trabajo o los componentes que quiera instalar. A continuación, elija **Modificar**.

### <a name="step-5---choose-individual-components-optional"></a>Paso 5: Elegir componentes individuales (opcional)

Si no quiere usar la característica Cargas de trabajo para personalizar la instalación de Visual Studio o quiere agregar más componentes de los que instala una carga de trabajo, puede hacerlo instalando o agregando componentes individuales desde la pestaña **Componentes individuales**. Elija los elementos que quiera y, luego, siga las indicaciones.

  ![Visual Studio 2019: instalar componentes individuales](../get-started/media/vs-installer-individual-components.png "Instalación de componentes individuales de Visual Studio")

### <a name="step-6---install-language-packs-optional"></a>Paso 6 - Instalar paquetes de idioma (opcional)

De manera predeterminada, el programa instalador intenta hacer coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. Para instalar Visual Studio en un idioma de su elección, elija la pestaña **Paquetes de idioma** del Instalador de Visual Studio y siga las indicaciones.

  ![Visual Studio 2019: instalar paquetes de idioma](../get-started/media/vs-installer-language-packs.png "Instalación de paquetes de idioma de Visual Studio")

#### <a name="change-the-installer-language-from-the-command-line"></a>Cambio del idioma del instalador en la línea de comandos

Otra manera de cambiar el idioma predeterminado es mediante la ejecución del instalador desde la línea de comandos. Por ejemplo, puede forzar al instalador a utilizar el inglés utilizando el comando siguiente: `vs_installer.exe --locale en-US`. El instalador recordará esta configuración cuando se ejecute la próxima vez. El instalador admite los siguientes tokens de idioma: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru y tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Paso 7: Cambiar la ubicación de instalación (opcional)

Puede reducir la superficie de memoria de instalación de Visual Studio en la unidad del sistema. Puede mover la caché de descarga, los componentes compartidos, SDK y herramientas a distintas unidades y mantener Visual Studio en la unidad que lo ejecuta más rápido.

  ![Visual Studio 2019: cambio de las ubicaciones de instalación](../get-started/media/vs-installer-installation-locations.png "Cambio de la ubicación de la instalación")

> [!IMPORTANT]
> Solo puede seleccionar una unidad diferente al instalar Visual Studio por primera vez. Si ya lo ha instalado y quiere cambiar de unidad, debe desinstalar Visual Studio y volver a instalarlo.

### <a name="step-8---start-developing"></a>Paso 8: Empezar a desarrollar

1. Cuando la instalación de Visual Studio haya finalizado, elija el botón **Iniciar** para empezar a desarrollar con Visual Studio.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

1. En el cuadro de búsqueda, escriba el tipo de aplicación que quiera crear para ver una lista de plantillas disponibles. La lista de plantillas depende de las cargas de trabajo que eligió durante la instalación. Para ver diferentes plantillas, elija diferentes cargas de trabajo.

   También puede filtrar la búsqueda de un lenguaje de programación específico mediante la lista desplegable **Lenguaje**. Además, puede filtrar mediante la lista **Plataforma** y la lista **Tipo de proyecto**.

1. Visual Studio abre el nuevo proyecto y ya se puede empezar programar.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalación de Visual Studio 2017

En Visual Studio 2017, resulta muy fácil elegir e instalar solo las características que se necesitan. Además, gracias a la mínima superficie de memoria que ocupa, se instala rápidamente y con menos impacto en el sistema.

### <a name="prerequisites"></a>Requisitos previos

- Una conexión a Internet de banda ancha. El Instalador de Visual Studio puede descargar varios gigabytes de datos.

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Recomendamos Windows 10 para obtener la mejor experiencia de desarrollo. Antes de instalar Visual Studio, asegúrese de que el sistema cuenta con las actualizaciones más recientes.

- Suficiente espacio libre en disco. Visual Studio necesita al menos 7 GB de espacio en disco y puede ocupar 50 GB o más si hay muchas opciones comunes instaladas. Se recomienda instalarlo en la unidad C:.

Para obtener información sobre los requisitos de espacio en disco y de sistema operativo, vea [Requisitos del sistema de la familia de productos de Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). El instalador informa de cuánto espacio en disco se necesita para las opciones que seleccione.

### <a name="download-and-install"></a>Descargar e instalar

1. Descargue el Instalador de Visual Studio 2017 más reciente para Windows.

   > [!div class="nextstepaction"]
   > [Instalar Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > La edición Community es para desarrolladores individuales, aprendizaje en el aula, investigación académica y desarrollo de código abierto. Para otros usos, instale [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) o [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Busque el archivo del instalador que se ha descargado y ejecútelo. Es posible que se muestre en el explorador o que se encuentre en la carpeta Descargas. El instalador necesita privilegios de administrador para ejecutarse. Es posible que vea un cuadro de diálogo de **Control de cuentas de usuario** que le pida conceder permiso para que el instalador realice cambios en el sistema. Elija **Sí**. Si tiene problemas, busque el archivo descargado en el Explorador de archivos, haga clic con el botón derecho en el icono del instalador y elija **Ejecutar como administrador** en el menú contextual.

   ![Descarga e instalación del Instalador de Visual Studio](media/vscpp-concierge-run-installer.gif "Descarga e instalación del Instalador de Visual Studio")

1. El instalador muestra una lista de las cargas de trabajo, que son grupos de opciones relacionadas para áreas de desarrollo específicas. La compatibilidad con C++ ahora forma parte de cargas de trabajo opcionales que no están instaladas de forma predeterminada.

   ![Desarrollo para el escritorio con la carga de trabajo de C++](media/desktop-development-with-cpp.png "Desarrollo para el escritorio con C++")

   En el caso de C++, seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y luego elija **Instalar**.

   ![Instalación del desarrollo para el escritorio con la carga de trabajo de C++](media/vscpp-concierge-choose-workload.gif "Instalación del desarrollo para el escritorio con la carga de trabajo de C++")

1. Cuando se complete la instalación, elija el botón **Iniciar** para abrir Visual Studio.

   La primera vez que ejecute Visual Studio, se le pedirá que inicie sesión con una cuenta de Microsoft. Si no tienes una, puedes crear una gratis. También se debe elegir un tema. No se preocupe, se puede cambiar más adelante si se quiere.

   Es posible que Visual Studio tarde varios minutos en estar listo para usar la primera vez que se ejecute. Este es su aspecto en un time-lapse rápido:

   ![Inicio de sesión en Visual Studio 2017](media/vscpp-quickstart-first-run.gif "Inicio de sesión en Visual Studio 2017")

   Visual Studio se inicia mucho más rápido cuando se vuelve a ejecutar.

1. Cuando se abra Visual Studio, compruebe si está resaltado el icono de marca de la barra de título:

   ![Marca de notificación en Visual Studio 2017](media/vscpp-first-start-page-flag.png "Marca de notificación en Visual Studio 2017")

   Si está resaltado, selecciónelo para abrir la ventana **Notificaciones**. Si hay actualizaciones disponibles para Visual Studio, se recomienda instalarlas ahora. Cuando la instalación finalice, reinicie Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Instalación de Visual Studio 2015

Para instalar Visual Studio 2015, vaya a [Descargar versiones anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Ejecute el programa de instalación y elija **Instalación personalizada** y, a continuación, seleccione el componente de C++. Para agregar compatibilidad con C++ a una instalación existente de Visual Studio 2015, haga clic en el botón Inicio de Windows y escriba **Agregar o quitar programas**. Abra el programa desde la lista de resultados y, después, busque la instalación de Visual Studio 2015 en la lista de programas instalados. Haga doble clic, elija **Modificar** y seleccione los componentes de Visual C++ que se van a instalar.

En general, recomendamos encarecidamente que use Visual Studio 2017, incluso para compilar el código mediante el compilador de Visual Studio 2015. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](../porting/use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

::: moniker-end

Cuando Visual Studio se esté ejecutando, estará a punto para continuar con el paso siguiente.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Creación de un proyecto de C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
