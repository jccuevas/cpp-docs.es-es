---
title: 'Cómo: usar el SDK de Windows 10 en una aplicación de escritorio de Windows'
description: Cómo establecer la versión del SDK de destino en un proyecto de aplicación de escritorio de Windows para usar el SDK de Windows 10.
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725739"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Cómo: usar el SDK de Windows 10 en una aplicación de escritorio de Windows

Cuando se crea un nuevo proyecto clásico de escritorio de Windows en Visual Studio, tiene como destino el SDK de Windows 10 de forma predeterminada. Visual Studio instala una versión de este SDK al instalar la carga de C++ trabajo del escritorio. El SDK de Windows 10 admite la escritura de código para Windows 7 SP1 y versiones posteriores. Para obtener más información sobre cómo establecer como destino versiones específicas de Windows, vea [usar los encabezados de Windows](/windows/win32/WinProg/using-the-windows-headers) y [actualizar winver y _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

Al actualizar un proyecto existente, tiene la opción de elegir: puede seguir usando los Windows SDK de destino especificados en el proyecto. O bien, puede redestinar el proyecto para que use el SDK de Windows 10. Con el SDK de Windows 10, obtendrá las ventajas de la compatibilidad con los sistemas operativos y los estándares de lenguaje más recientes.

## <a name="use-the-right-windows-sdk-for-your-project"></a>Usar el Windows SDK correcto para el proyecto

A partir de Visual Studio 2015, la biblioteca en tiempo de ejecución de C (CRT) se separó en dos partes: una parte, ucrtbase, contiene las funciones de CRT estándar de C y específicas de Microsoft que puede usar en aplicaciones universales de Windows. Esta biblioteca ahora se conoce como CRT universal, o UCRT, y se ha pasado al SDK de Windows 10. UCRT contiene muchas funciones nuevas, como las funciones C99, necesarias para admitir los estándares de C++ lenguaje más recientes. La otra parte del CRT original es vcruntime. Contiene el código de compatibilidad, Inicio y terminación en tiempo de ejecución de C, y todo lo demás que no se encontraba en el UCRT. La biblioteca vcruntime se instala junto con el C++ compilador y el conjunto de herramientas en Visual Studio. Para obtener más información, vea características de la [biblioteca CRT](../c-runtime-library/crt-library-features.md).

UCRT es ahora un componente del sistema que se instala en todas las versiones de Windows 10. También está disponible como componente instalable para todas las versiones anteriores compatibles de Windows. Puede usar el SDK de Windows 10 para tener como destino todas las versiones compatibles de Windows. Para obtener una lista completa de los sistemas operativos compatibles, consulte el [SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Para redestinar los proyectos para que usen el SDK de Windows 10 al actualizar desde una versión de proyecto anterior a Visual Studio 2015, siga estos pasos:

### <a name="to-target-the-windows-10-sdk"></a>Para elegir como destino el SDK de Windows 10

1. Asegúrese de que esté instalado el SDK de Windows 10. El SDK de Windows 10 se instala como parte del **desarrollo de escritorio C++ con** carga de trabajo. Hay disponible una versión independiente en [descargas y herramientas para Windows 10](https://developer.microsoft.com/windows/downloads).

1. Abra el menú contextual del nodo del proyecto y elija **redestinar proyectos**. (En versiones anteriores de Visual Studio, elija **redestinar versión del SDK**). Aparece el cuadro de diálogo **revisar acciones de solución** .

   ![Revisar las acciones de la solución](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. En la lista desplegable versión de la **plataforma de destino** , elija la versión del SDK de Windows 10 que quiere usar como destino. En general, se recomienda elegir la última versión instalada. Elija el botón **Aceptar** para aplicar el cambio.

   8,1 en este contexto hace referencia al SDK de Windows 8.1.

   Si este paso se realiza correctamente, aparecerá el siguiente texto en la ventana de salida:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. Abra el cuadro de diálogo Propiedades del proyecto. En las **propiedades de configuración** > sección **General** , observe los valores de versión de la **plataforma de destino de Windows**. Cambiar el valor aquí tiene el mismo efecto que seguir este procedimiento. Para obtener más información, vea [Página de propiedades General (Proyecto)](../build/reference/general-property-page-project.md).

   ![Versión de la plataforma de destino](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Esta acción cambia los valores de las macros del proyecto que incluyen rutas de acceso a archivos de encabezado y archivos de biblioteca. Para ver lo que ha cambiado, abra la sección **directorios C++ visuales** del cuadro de diálogo **propiedades del proyecto** . Seleccione una de las propiedades, como **directorios de inclusión**. A continuación, abra la lista desplegable del valor de propiedad y elija **\<editar >** . Se mostrará el diálogo **Directorios de archivos de inclusión** .

   ![Cuadro de diálogo directorios de inclusión](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Elija el botón **macros > >** y desplácese hacia abajo en la lista de macros hasta la Windows SDK macros para ver todos los valores nuevos.

   ![Macros Windows SDK](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. Repita el procedimiento de redestinación para otros proyectos de la solución, según sea necesario, y vuelva a generar la solución.

### <a name="to-target-the-windows-81-sdk"></a>Para elegir como destino el SDK de Windows 8.1

1. Abra el menú contextual del nodo de proyecto en Explorador de soluciones y elija **redestinar proyectos**. (En versiones anteriores de Visual Studio, elija **redestinar versión del SDK**).

2. En la lista desplegable versión de la **plataforma de destino** , elija **8,1**.

## <a name="see-also"></a>Vea también

[Tutorial: crear una aplicación de escritorio de WindowsC++tradicional ()](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
