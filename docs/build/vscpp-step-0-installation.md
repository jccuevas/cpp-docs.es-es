---
title: Instalar compatibilidad de C++ en Visual Studio | Documentos de Microsoft
description: Instalar la compatibilidad de Visual Studio para Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b895569e5535fb05c1e2383df224f149815dd47f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="install-c-support-in-visual-studio"></a>Instalar compatibilidad de C++ en Visual Studio

Si no ha descargado e instalado Visual Studio y las herramientas de Visual C++ aún, aquí se muestra cómo empezar a trabajar.

## <a name="prerequisites"></a>Requisitos previos

- Una conexión de internet de banda ancha. El instalador de Visual Studio puede descargar varios gigabytes de datos.

- Un equipo que ejecuta Microsoft Windows 7 o versiones posteriores. Se recomienda Windows 10 para una mejor experiencia de desarrollo. Asegúrese de que se aplican las actualizaciones más recientes en el sistema antes de instalar Visual Studio.

- Suficiente espacio libre en disco. Visual Studio requiere al menos 7GB de espacio en disco y puede tardar 50GB o más si se instalan muchas opciones comunes. Se recomienda que instale en la unidad C:.

Para obtener detalles sobre los requisitos de sistema operativo y espacio en disco, consulte [requisitos de sistema de Visual Studio de 2017](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). El programa de instalación indica cuánto espacio en disco necesario para las opciones que seleccione.

## <a name="installation"></a>Instalación

1. Descargar al instalador de Visual Studio de 2017 más reciente de Windows.

   > [!div class="nextstepaction"]
   > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&utm_source=docs&utm_medium=clickbutton">Instalar Visual Studio 2017 Community</a>

   >[!Tip]
   > La edición Community es para desarrolladores individuales, aprendizaje en el aula, investigación académica y desarrollo de código abierto. Para otros usos, instale <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Professional</a> o <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Enterprise</a>.

1. Busque el archivo de instalador descargado y ejecútelo. Puede mostrarse en el explorador, o se puede encontrar en la carpeta de descargas. El instalador necesita privilegios de administrador para ejecutar. Es posible que vea una **User Account Control** cuadro de diálogo que le pide que conceder permiso para permitir que el programa de instalación realizar cambios en el sistema; elegir **Sí**. Si tiene problemas, busque el archivo descargado en el Explorador de archivos, haga doble clic en el icono de programa de instalación y elija **ejecutar como administrador** en el menú contextual.

   ![Ejecute el instalador de Visual Studio de 2017](../build/media/vscpp-concierge-run-installer.gif "ejecute el instalador de Visual Studio")

1. El instalador muestra una lista de las cargas de trabajo, que son grupos de opciones relacionadas para áreas de desarrollo específicas. Compatibilidad de C++ ahora forma parte de las cargas de trabajo opcionales que no se instala de forma predeterminada.

   ![Desarrollo de escritorio con C++](../build/media/desktop-development-with-cpp.png "el desarrollo de escritorio con C++")

    En C++, seleccione el **el desarrollo de escritorio con C++** carga de trabajo y, a continuación, elija **instalar**.

   ![Instalar el desarrollo de escritorio con cargas de trabajo de C++](../build/media/vscpp-concierge-choose-workload.gif "instalar el desarrollo de escritorio con cargas de trabajo de C++")

1. Cuando se complete la instalación, elija la **iniciar** botón para iniciar Visual Studio.

   La primera vez que ejecute Visual Studio, deberá iniciar sesión con una Account de Microsoft. Si no tiene uno, puede crearlo de forma gratuita. También debe elegir un tema. No se preocupe, puede cambiar más adelante si desea. 

   Puede tardar Visual Studio varios minutos para preparar de la primera vez que se ejecuta. Este es su aspecto en una lapso de tiempo rápida:

   ![Iniciar sesión Visual Studio de 2017](../build/media/vscpp-quickstart-first-run.gif "2017 de Visual Studio que inicie sesión en")

   Visual Studio inicia mucho más rápidamente cuando vuelva a ejecutarlo.

1. Cuando se abre Visual Studio, compruebe si el icono de marca en la barra de título se resalta:

   ![Marca de notificación de Visual Studio de 2017](../build/media/vscpp-first-start-page-flag.png "marca de notificación de 2017 de Visual Studio")

   Si está resaltado, selecciónela para abrir el **notificaciones** ventana. Si hay actualizaciones disponibles para Visual Studio, se recomienda que instalar ahora. Una vez completada la instalación, reinicie Visual Studio.

Cuando se está ejecutando Visual Studio, estará listo para continuar con el paso siguiente.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Crear un proyecto de C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
