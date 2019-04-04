---
title: Instalar compatibilidad con C++ en Visual Studio
description: Instalar la compatibilidad de Visual Studio para Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 5fc76f5b3c4c3ee49f38f05b37261a324591530b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58870785"
---
# <a name="install-c-support-in-visual-studio"></a>Instalar compatibilidad con C++ en Visual Studio

Si aún no ha descargado e instalado Visual Studio y las herramientas de Visual C++ aún, aquí le mostramos cómo empezar a trabajar.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Instalación de Visual Studio de 2019

Bienvenido a Visual Studio de 2019. En esta versión, es fácil elegir e instalar las características que necesita. Y debido a su impacto mínimo reducido, lo instala rápidamente y con menos impacto del sistema.

> [!NOTE]
> En este tema se aplica a la instalación de Visual Studio en Windows. [Código de Visual Studio](https://code.visualstudio.com/) es un entorno de desarrollo ligera y multiplataforma que se ejecuta en sistemas Windows, Mac y Linux. Microsoft [C o C++ para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) extensión es compatible con IntelliSense, depuración, formato, finalización automática de código. Visual Studio para Mac no es compatible con Microsoft C++, pero es compatible con lenguajes .NET y el desarrollo multiplataforma. Para obtener instrucciones de instalación, consulte [instalar Visual Studio para Mac](/visualstudio/mac/installation/).

¿Quiere saber más sobre otras novedades de esta versión? Vea Visual Studio [notas de la versión](/visualstudio/releases/2019/release-notes/).

¿Está listo para instalarlo? Le guiaremos paso a paso.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Paso 1: Asegurarse de que el equipo está listo para Visual Studio

Antes de comenzar la instalación de Visual Studio:

1. Compruebe los [requisitos del sistema](/visualstudio/releases/2019/system-requirements). Estos requisitos le permiten saber si su equipo es compatible con Visual Studio de 2019.

1. Aplique las actualizaciones de Windows más recientes. Estas actualizaciones garantizan que el equipo tiene las actualizaciones de seguridad más recientes y los componentes del sistema necesarios para Visual Studio.

1. Reinicie el equipo. El reinicio garantiza que cualquier actualización o instalación pendiente no dificultará la instalación de Visual Studio.

1. Libere espacio. Quite los archivos y aplicaciones innecesarios de %SystemDrive% ejecutando, por ejemplo, la aplicación Liberar espacio.

Para ver las preguntas sobre la ejecución de las versiones anteriores de Visual Studio en paralelo con Visual Studio de 2019, el [compatibilidad y destinatarios de Visual Studio 2019 plataforma](/visualstudio/releases/2019/compatibility/) página.

### <a name="step-2---download-visual-studio"></a>Paso2: Descargar Visual Studio

A continuación, descargue el archivo de programa previo de Visual Studio. Para ello, elija el botón siguiente, elija la edición de Visual Studio que desee, elija **guardar**y, a continuación, elija **Abrir carpeta**.

 > [!div class="button"]
 > [Descargue Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Paso 3: Desinstalar el Instalador de Visual Studio

Ejecute el archivo de programa previo para instalar al instalador de Visual Studio. Este nuevo instalador ligero incluye todo lo que necesita para instalar y personalizar Visual Studio.

1. Desde la carpeta **Descargas**, haga doble clic en el archivo de programa previo que coincida o sea similar a uno de los siguientes archivos:

   * **vs_community.exe** para Visual Studio Community
   * **vs_professional.exe** para Visual Studio Professional
   * **vs_enterprise.exe** para Visual Studio Enterprise

   Si recibe un aviso de Control de cuentas de usuario, elija **Sí**.

1. Le pediremos que acepte los [Términos de licencia](https://visualstudio.microsoft.com/license-terms/) de Microsoft y la [Declaración de privacidad](https://privacy.microsoft.com/privacystatement) de Microsoft. Elija **continuar**.

### <a name="step-4---choose-workloads"></a>Paso 4: elegir las cargas de trabajo

Después de instala el programa de instalación, puede usar para personalizar la instalación seleccionando la *cargas de trabajo*, o una característica de conjuntos, que desee. Esta es la manera de hacerlo.

1. Busque la carga de trabajo que quiera en la pantalla **Instalando Visual Studio**.

   ![Visual Studio 2019: Instalar una carga de trabajo](../get-started/media/vs-installer-workloads.png)

   Para obtener soporte técnico de C++ principal, elija la carga de trabajo "Desarrollo de escritorio con C++". Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.

   Cargas de trabajo adicionales admiten otros tipos de desarrollo de C++. Por ejemplo, elija la carga de trabajo "Desarrollo de plataforma Universal de Windows" para crear aplicaciones que usan el tiempo de ejecución de Windows para la Microsoft Store. Elija "Desarrollo de juegos con C++" para crear juegos que usan DirectX, Unreal y Cocos2d. Elija "Desarrollo de Linux con C++" para plataformas Linux de destino, incluido el desarrollo de IoT.

   El **detalles de la instalación** panel muestra los componentes opcionales e incluye instalados por cada carga de trabajo. Puede seleccionar o anular la selección de componentes opcionales en esta lista. Por ejemplo, para admitir el desarrollo mediante conjuntos de herramientas del compilador 2015 o Visual Studio 2017, elija el MSVC v141 o componentes opcionales de MSVC v140. Puede agregar compatibilidad con MFC, la extensión del lenguaje de módulos experimental, IncrediBuild y mucho más.

1. Después de elegir las cargas de trabajo y componentes opcionales que desee, elija **instalar**.

    Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

> [!TIP]
> En cualquier momento después de la instalación, puede instalar las cargas de trabajo o los componentes que no instaló inicialmente. Si tiene Visual Studio abierto, vaya a **Herramientas** > **Obtener herramientas y características...** para abrir el Instalador de Visual Studio. O bien, abra el **Instalador de Visual Studio** desde el menú Inicio. Desde allí, puede elegir los componentes que desea instalar o las cargas de trabajo. A continuación, elija **modificar**.

## <a name="step-5---choose-individual-components-optional"></a>Paso 5: seleccionar componentes individuales (opcional)

Si no desea usar la característica de las cargas de trabajo para personalizar la instalación de Visual Studio, o que desea agregar más componentes que instala una carga de trabajo, puede hacerlo mediante la instalación o agregar componentes individuales desde la **loscomponentesindividuales** ficha. Elija lo que desee y, a continuación, siga las indicaciones.

  ![Visual Studio 2019 - instalar componentes individuales](../get-started/media/vs-installer-individual-components.png "componentes individuales de instalación de Visual Studio")

## <a name="step-6---install-language-packs-optional"></a>Paso 6 - Instalar paquetes de idioma (opcional)

De manera predeterminada, el programa instalador intenta hacer coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. Para instalar Visual Studio en un lenguaje de su elección, elija el **paquetes de idioma** ficha desde el instalador de Visual Studio y, a continuación, siga las indicaciones.

  ![Visual Studio 2019 - instalar paquetes de idioma](../get-started/media/vs-installer-language-packs.png "paquetes de idioma de instalación de Visual Studio")

### <a name="change-the-installer-language-from-the-command-line"></a>Cambio del idioma del instalador en la línea de comandos

Otra manera de cambiar el idioma predeterminado es mediante la ejecución del instalador desde la línea de comandos. Por ejemplo, puede forzar al instalador a utilizar el inglés utilizando el comando siguiente: `vs_installer.exe --locale en-US`. El instalador recordará esta configuración cuando se ejecuta la próxima vez. El instalador admite los siguientes tokens de idioma: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru y tr-tr.

### <a name="step-7---change-the-installation-location-optional"></a>Paso 7: Cambiar la ubicación de instalación (opcional)

Puede reducir la superficie de instalación de Visual Studio en la unidad del sistema. Puede mover la caché de descarga, los componentes compartidos, SDK y herramientas a distintas unidades y mantener Visual Studio en la unidad que lo ejecuta más rápido.

  ![Visual Studio 2019 - ubicaciones de instalación de cambio](../get-started/media/vs-installer-installation-locations.png "cambiar la ubicación de instalación")

> [!IMPORTANT]
> Puede seleccionar una unidad diferente solo al instalar primero Visual Studio. Si ya ha instalado y desea cambiar las unidades, debe desinstalar Visual Studio y, a continuación, vuelva a instalarlo.

## <a name="step-8---start-developing"></a>Paso 8: Empezar a desarrollar

1. Una vez completada la instalación de Visual Studio, elija el **iniciar** botón para comenzar a desarrollar con Visual Studio.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

1. En el cuadro de búsqueda, escriba el tipo de aplicación que desea crear para ver una lista de plantillas disponibles. La lista de plantillas depende de las cargas de trabajo que eligió durante la instalación. Para ver diferentes plantillas, elija diferentes cargas de trabajo.

   También puede filtrar la búsqueda de un lenguaje de programación específico mediante el **lenguaje** lista desplegable. Puede filtrar mediante el **plataforma** lista y **tipo de proyecto** enumerar, demasiado.

1. Visual Studio abre el nuevo proyecto, y está listo para código!

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Instalación de Visual Studio 2017

En Visual Studio 2017, es fácil elegir e instalar las características que necesita. Y debido a su impacto mínimo reducido, lo instala rápidamente y con menos impacto del sistema.

### <a name="prerequisites"></a>Requisitos previos

- Una conexión de banda ancha. El instalador de Visual Studio puede descargar varios gigabytes de datos.

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo. Asegúrese de que se aplican las actualizaciones más recientes en el sistema antes de instalar Visual Studio.

- Hay suficiente espacio libre en disco. Visual Studio requiere al menos 7 GB de espacio en disco y puede tardar 50 GB o más si muchas de las opciones están instalados. Se recomienda que instale en la unidad C:.

Para obtener más información sobre el espacio en disco y requisitos del sistema operativo, consulte [requisitos del sistema de familia de productos de Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). El programa de instalación notifica cuánto espacio en disco es necesario para las opciones que seleccione.

### <a name="download-and-install"></a>Descarga e instalación

1. Descargue al instalador de Visual Studio 2017 más reciente para Windows.

   > [!div class="nextstepaction"]
   > [Instalar Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > La edición Community es para desarrolladores individuales, aprendizaje en el aula, investigación académica y desarrollo de código abierto. Para otros usos, instale [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) o [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Busque el archivo de instalador que descargó y ejecútelo. Se pueden mostrar en el explorador o se puede encontrar en la carpeta de descargas. El instalador necesita privilegios de administrador para ejecutarse. Es posible que vea un **User Account Control** cuadro de diálogo que le pide que conceder permiso para permitir que el programa de instalación realizar cambios en el sistema; elija **Sí**. Si tiene problemas, busque el archivo descargado en el Explorador de archivos, haga doble clic en el icono de programa de instalación y elija **ejecutar como administrador** en el menú contextual.

   ![Descargue e instale el instalador de Visual Studio](media/vscpp-concierge-run-installer.gif "descargue e instale el instalador de Visual Studio")

1. El instalador muestra una lista de las cargas de trabajo, que son grupos de opciones relacionadas para áreas de desarrollo específicas. Compatibilidad de C++ ahora forma parte de las cargas de trabajo opcionales que no están instaladas de forma predeterminada.

   ![Desarrollo de escritorio con la carga de trabajo de C++](media/desktop-development-with-cpp.png "desarrollo de escritorio con C++")

   Para C++, seleccione el **desarrollo de escritorio con C++** carga de trabajo y, a continuación, elija **instalar**.

   ![Instalar el desarrollo de escritorio con la carga de trabajo de C++](media/vscpp-concierge-choose-workload.gif "instalar el desarrollo de escritorio con la carga de trabajo de C++")

1. Cuando se complete la instalación, elija la **iniciar** botón para iniciar Visual Studio.

   La primera vez que ejecute Visual Studio, se le pide que inicie sesión con una Account de Microsoft. Si no tiene una, puede crear una gratis. También debe elegir un tema. No se preocupe, puede cambiar más adelante si desea.

   Puede tardar Visual Studio varios minutos para que esté listo para usar la primera vez que se ejecuta. Este es su aspecto en un lapso de tiempo rápido:

   ![Inicie Visual Studio 2017](media/vscpp-quickstart-first-run.gif "sesión Visual Studio 2017")

   Visual Studio inicia mucho más rápido cuando se ejecuta de nuevo.

1. Cuando se abre Visual Studio, compruebe si se resalta el icono de marca en la barra de título:

   ![Marca de notificación de Visual Studio 2017](media/vscpp-first-start-page-flag.png "marca de notificación de Visual Studio 2017")

   Si está resaltado, selecciónela para abrir el **notificaciones** ventana. Si hay actualizaciones disponibles para Visual Studio, se recomienda que instalar ahora. Una vez completada la instalación, reinicie Visual Studio.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Instalación de Visual Studio 2015

Para instalar Visual Studio 2015, vaya a [Descargar versiones anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Ejecute el programa de instalación y elija **Instalación personalizada** y, a continuación, seleccione el componente de C++. Para agregar compatibilidad de C++ a una instalación existente de Visual Studio 2015, haga clic en el botón Inicio de Windows y el tipo **agregar o quitar programas**. Abra el programa desde la lista de resultados y, a continuación, busque la instalación de Visual Studio 2015 en la lista de programas instalados. Haga doble clic en él y luego elija **modificar** y seleccione los componentes de Visual C++ para instalar.

En general, recomendamos encarecidamente que use Visual Studio 2017, incluso para compilar el código mediante el compilador de Visual Studio 2015. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](../porting/use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

::: moniker-end

Cuando se está ejecutando Visual Studio, está listo para continuar con el paso siguiente.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear un proyecto de C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
