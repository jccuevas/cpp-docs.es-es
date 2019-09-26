---
title: Procedimiento Usar el SDK de Windows 10 en una aplicación de escritorio de Windows
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 8dbf18d24c0369507743c3c1da624838f9ab4703
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "69513821"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Procedimiento Usar el SDK de Windows 10 en una aplicación de escritorio de Windows

Cuando se crea un proyecto de escritorio clásico de Windows en Visual Studio 2017, se configura de forma predeterminada para compilar con la versión del SDK de Windows 10 que se C++ instaló al instalar o actualizar por última vez la carga de trabajo de escritorio. Esta versión del Windows SDK es compatible con Windows 7 y versiones posteriores. Vea [usar los encabezados de Windows](/windows/win32/WinProg/using-the-windows-headers) para obtener más información sobre cómo establecer como destino versiones específicas de Windows.

Si desea tener como destino una versión anterior del SDK, puede abrir el **proyecto | Propiedades** y elija entre las otras versiones del SDK disponibles en la lista desplegable Windows SDK versión.

A partir de Visual Studio 2015 y el SDK de Windows 10, la biblioteca de CRT se separó en dos partes: una (ucrtbase) que contiene las funciones que son aceptables para su uso en aplicaciones universales de Windows y otra que contiene todo lo demás (vcruntime140). Puesto que el SDK de Windows 10 contiene nuevas funciones como, por ejemplo, muchas funciones de C99, tendrá que seguir estos pasos para usar esas funciones. Vea [CRT Library Features](../c-runtime-library/crt-library-features.md).

### <a name="to-target-the-windows-10-sdk"></a>Para elegir como destino el SDK de Windows 10

1. Asegúrese de que esté instalado el SDK de Windows 10. El SDK de Windows 10 se instala como parte del **desarrollo de escritorio C++ con** carga de trabajo. Hay disponible una versión independiente en [descargas y herramientas para Windows 10](https://developer.microsoft.com/windows/downloads).

2. Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.

   ![Versión del SDK de redestinación](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   Se mostrará el diálogo **Revisar acciones de solución** .

   ![Revisar las acciones] de la solución (../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. En la lista desplegable versión de la **plataforma de destino** , elija la versión del SDK de Windows 10 que quiere usar como destino. Elija el botón Aceptar para aplicar el cambio.

   Tenga en cuenta que 8.1, en este contexto, hace referencia a la versión del SDK de Windows, que también es compatible con Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 y Windows Vista.

   Si este paso se realiza correctamente, aparecerá el siguiente texto en la ventana de salida:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. Abra las propiedades del proyecto y, en la sección **Propiedades de configuración, General** , observe los valores de **Versión de plataforma de destino de Windows**. Cambiar el valor aquí tiene el mismo efecto que seguir este procedimiento. Vea [General Property Page (Project)](../build/reference/general-property-page-project.md).

   ![Versión] de la plataforma de destino (../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Esta acción cambia los valores de las macros del proyecto que incluyen rutas de acceso a archivos de encabezado y archivos de biblioteca. Para ver lo que ha cambiado, en la sección **directorios C++ visuales** del cuadro de diálogo **propiedades del proyecto** , elija una de las propiedades, como los directorios de **inclusión**, elija para abrir la \<lista desplegable y elija Editar >. Se mostrará el diálogo **Directorios de archivos de inclusión** .

   ![Cuadro de diálogo directorios de inclusión](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Elija el botón **macros > >** y desplácese hacia abajo en la lista de macros hasta la Windows SDK macros para ver todos los valores nuevos.

   ![Macros Windows SDK](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. Repita este procedimiento con los demás proyectos si es necesario y vuelva a compilar la solución.

### <a name="to-target-the-windows-81-sdk"></a>Para elegir como destino el SDK de Windows 8.1

1. Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.

2. En la lista desplegable versión de la **plataforma de destino** , elija **8,1**.

## <a name="see-also"></a>Vea también

[Aplicaciones de escritorio de Windows C++(visual)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)