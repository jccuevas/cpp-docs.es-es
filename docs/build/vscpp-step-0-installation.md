---
title: Instalar compatibilidad con C++ en Visual Studio | Microsoft Docs
description: Instalar la compatibilidad de Visual Studio para Visual C++
ms.custom: mvc
ms.date: 06/21/2018
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cc9c124a5b3f2fea92f729d7d11df579cc25a39
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376064"
---
# <a name="install-c-support-in-visual-studio"></a>Instalar compatibilidad con C++ en Visual Studio

Si aún no ha descargado e instalado Visual Studio y las herramientas de Visual C++ aún, aquí le mostramos cómo empezar a trabajar.

## <a name="prerequisites"></a>Requisitos previos

- Una conexión de banda ancha. El instalador de Visual Studio puede descargar varios gigabytes de datos.

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo. Asegúrese de que se aplican las actualizaciones más recientes en el sistema antes de instalar Visual Studio.

- Hay suficiente espacio libre en disco. Visual Studio requiere al menos 7GB de espacio en disco y puede tardar 50GB o más si muchas de las opciones están instalados. Se recomienda que instale en la unidad C:.

Para obtener más información sobre el espacio en disco y requisitos del sistema operativo, consulte [requisitos del sistema de familia de productos de Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs). El programa de instalación notifica cuánto espacio en disco es necesario para las opciones que seleccione.

## <a name="installation"></a>Instalación

1. Descargue al instalador de Visual Studio 2017 más reciente para Windows.

   > [!div class="nextstepaction"]
   > [Instalar Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > La edición Community es para desarrolladores individuales, aprendizaje en el aula, investigación académica y desarrollo de código abierto. Para otros usos, instale <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Visual Studio 2017 Professional</a> o <a target="frameTarget" href="https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017">Visual Studio 2017 Enterprise</a>.

1. Busque el archivo de instalador que descargó y ejecútelo. Se pueden mostrar en el explorador o se puede encontrar en la carpeta de descargas. El instalador necesita privilegios de administrador para ejecutarse. Es posible que vea un **User Account Control** cuadro de diálogo que le pide que conceder permiso para permitir que el programa de instalación realizar cambios en el sistema; elija **Sí**. Si tiene problemas, busque el archivo descargado en el Explorador de archivos, haga doble clic en el icono de programa de instalación y elija **ejecutar como administrador** en el menú contextual.

   ![Ejecute el instalador de Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "ejecute el instalador de Visual Studio")

1. El instalador muestra una lista de las cargas de trabajo, que son grupos de opciones relacionadas para áreas de desarrollo específicas. Compatibilidad de C++ ahora forma parte de las cargas de trabajo opcionales que no están instaladas de forma predeterminada.

   ![Desarrollo de escritorio con C++](../build/media/desktop-development-with-cpp.png "desarrollo de escritorio con C++")

    Para C++, seleccione el **desarrollo de escritorio con C++** carga de trabajo y, a continuación, elija **instalar**.

   ![Instalar el desarrollo de escritorio con la carga de trabajo de C++](../build/media/vscpp-concierge-choose-workload.gif "instalar el desarrollo de escritorio con la carga de trabajo de C++")

1. Cuando se complete la instalación, elija la **iniciar** botón para iniciar Visual Studio.

   La primera vez que ejecute Visual Studio, deberá iniciar sesión con una Account de Microsoft. Si no tiene una, puede crear una gratis. También debe elegir un tema. No se preocupe, puede cambiar más adelante si desea. 

   Puede tardar Visual Studio varios minutos para preparar la primera vez que ejecutarlo. Este es su aspecto en un lapso de tiempo rápido:

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
