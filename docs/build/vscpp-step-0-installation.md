---
title: Instalar compatibilidad con C++ en Visual Studio 2017
description: Instalar la compatibilidad de Visual Studio para Visual C++
ms.custom: mvc
ms.date: 09/17/2018
ms.topic: tutorial
ms.devlang: C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 019eadee35829bb546de0a69707520dc98f4077e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507242"
---
# <a name="install-c-support-in-visual-studio"></a>Instalar compatibilidad con C++ en Visual Studio

Si aún no ha descargado e instalado Visual Studio 2017 y las herramientas de Visual C++ aún, aquí le mostramos cómo empezar a trabajar.

## <a name="prerequisites"></a>Requisitos previos

- Una conexión de banda ancha. El instalador de Visual Studio puede descargar varios gigabytes de datos.

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo. Asegúrese de que se aplican las actualizaciones más recientes en el sistema antes de instalar Visual Studio.

- Hay suficiente espacio libre en disco. Visual Studio requiere al menos 7GB de espacio en disco y puede tardar 50GB o más si muchas de las opciones están instalados. Se recomienda que instale en la unidad C:.

Para obtener más información sobre el espacio en disco y requisitos del sistema operativo, consulte [requisitos del sistema de familia de productos de Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). El programa de instalación notifica cuánto espacio en disco es necesario para las opciones que seleccione.

## <a name="visual-studio-2015-installation"></a>Instalación de Visual Studio 2015

Para instalar Visual Studio 2015, vaya a [Descargar versiones anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Ejecute el programa de instalación y elija **Instalación personalizada** y, a continuación, seleccione el componente de C++. Para agregar compatibilidad de C++ a una instalación existente de Visual Studio 2015, haga clic en el botón Inicio de Windows y el tipo **agregar o quitar programas**. Abra el programa desde la lista de resultados y, a continuación, busque la instalación de Visual Studio 2015 en la lista de programas instalados. Haga doble clic en él y luego elija **modificar** y seleccione los componentes de Visual C++ para instalar.

En general, recomendamos encarecidamente que use Visual Studio 2017, incluso para compilar el código mediante el compilador de Visual Studio 2015. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](../porting/use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

## <a name="visual-studio-2017-installation"></a>Instalación de Visual Studio 2017

1. Descargue al instalador de Visual Studio 2017 más reciente para Windows.

   > [!div class="nextstepaction"]
   > [Instalar Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > La edición Community es para desarrolladores individuales, aprendizaje en el aula, investigación académica y desarrollo de código abierto. Para otros usos, instale [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) o [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Busque el archivo de instalador que descargó y ejecútelo. Se pueden mostrar en el explorador o se puede encontrar en la carpeta de descargas. El instalador necesita privilegios de administrador para ejecutarse. Es posible que vea un **User Account Control** cuadro de diálogo que le pide que conceder permiso para permitir que el programa de instalación realizar cambios en el sistema; elija **Sí**. Si tiene problemas, busque el archivo descargado en el Explorador de archivos, haga doble clic en el icono de programa de instalación y elija **ejecutar como administrador** en el menú contextual.

   ![Ejecute el instalador de Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "ejecute el instalador de Visual Studio")

1. El instalador muestra una lista de las cargas de trabajo, que son grupos de opciones relacionadas para áreas de desarrollo específicas. Compatibilidad de C++ ahora forma parte de las cargas de trabajo opcionales que no están instaladas de forma predeterminada.

   ![Desarrollo de escritorio con C++](../build/media/desktop-development-with-cpp.png "desarrollo de escritorio con C++")

   Para C++, seleccione el **desarrollo de escritorio con C++** carga de trabajo y, a continuación, elija **instalar**.

   ![Instalar el desarrollo de escritorio con la carga de trabajo de C++](../build/media/vscpp-concierge-choose-workload.gif "instalar el desarrollo de escritorio con la carga de trabajo de C++")

1. Cuando se complete la instalación, elija la **iniciar** botón para iniciar Visual Studio.

   La primera vez que ejecute Visual Studio, deberá iniciar sesión con una Account de Microsoft. Si no tiene una, puede crear una gratis. También debe elegir un tema. No se preocupe, puede cambiar más adelante si desea.

   Puede tardar Visual Studio varios minutos para que esté listo para usar la primera vez que se ejecuta. Este es su aspecto en un lapso de tiempo rápido:

   ![Inicie Visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "sesión Visual Studio 2017")

   Visual Studio inicia mucho más rápido cuando se ejecuta de nuevo.

1. Cuando se abre Visual Studio, compruebe si se resalta el icono de marca en la barra de título:

   ![Marca de notificación de Visual Studio 2017](../build/media/vscpp-first-start-page-flag.png "marca de notificación de Visual Studio 2017")

   Si está resaltado, selecciónela para abrir el **notificaciones** ventana. Si hay actualizaciones disponibles para Visual Studio, se recomienda que instalar ahora. Una vez completada la instalación, reinicie Visual Studio.

Cuando se está ejecutando Visual Studio, está listo para continuar con el paso siguiente.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear un proyecto de C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
