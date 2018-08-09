---
title: 'Cómo: usar Windows 10 SDK en una aplicación de escritorio de Windows | Microsoft Docs'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 937afdb400fff6f0944d8690412257cb66a9c25c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018002"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Procedimiento de uso del SDK de Windows 10 en una aplicación de escritorio de Windows
Al crear un proyecto de escritorio clásico de Windows en Visual Studio 2017, se configura de forma predeterminada para compilar con la versión del SDK de Windows 10 que se instaló cuando la carga de trabajo de escritorio de C++ se instaló o actualizó por última vez. Esta versión del SDK de Windows es compatible con Windows 7 y versiones posteriores. Consulte [mediante los encabezados de Windows](/windows/desktop/WinProg/using-the-windows-headers) para obtener más información sobre cómo destinar versiones específicas de Windows.

Si desea tener como destino una versión anterior del SDK, puede abrir **proyecto | Propiedades** y elegir entre las demás versiones del SDK disponibles en la lista desplegable de la versión del SDK de Windows.
  
 Desde Visual Studio 2015 y el SDK de Windows 10, la biblioteca CRT se divide en dos partes, una (ucrtbase) que contiene las funciones que son aceptables para su uso en aplicaciones universales de Windows y que contiene todo lo demás (vcruntime140). Puesto que el SDK de Windows 10 contiene nuevas funciones como, por ejemplo, muchas funciones de C99, tendrá que seguir estos pasos para usar esas funciones. Consulte [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Para elegir como destino el SDK de Windows 10  
  
1.  Asegúrese de que esté instalado el SDK de Windows 10. El SDK de Windows 10 se instala como parte de la **desarrollo de escritorio con C++** carga de trabajo. Hay disponible una versión independiente en [descargas y herramientas para Windows 10](https://developer.microsoft.com/windows/downloads).

2.  Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.  
  
     ![Redestinar versión de SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     Se mostrará el diálogo **Revisar acciones de solución** .  
  
     ![Revisar acciones de solución](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  En el **versión de la plataforma de destino** lista desplegable, elija la versión de destino el SDK de Windows 10. Elija el botón Aceptar para aplicar el cambio.  
  
     Tenga en cuenta que 8.1, en este contexto, hace referencia a la versión del SDK de Windows, que también es compatible con Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 y Windows Vista.  
  
     Si este paso se realiza correctamente, aparecerá el siguiente texto en la ventana de salida:  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Abra las propiedades del proyecto y, en la sección **Propiedades de configuración, General** , observe los valores de **Versión de plataforma de destino de Windows**. Cambiar el valor aquí tiene el mismo efecto que seguir este procedimiento. Vea [General Property Page (Project)](../ide/general-property-page-project.md).  
  
     ![Versión de la plataforma de destino](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Esta acción cambia los valores de las macros del proyecto que incluyen rutas de acceso a archivos de encabezado y archivos de biblioteca. Para ver qué ha cambiado en el **directorios de Visual C++** sección de la **las propiedades del proyecto** cuadro de diálogo, elija una de las propiedades, como el **directorios de inclusión**, elegir Abra la lista desplegable y elija \<Editar >. Se mostrará el diálogo **Directorios de archivos de inclusión** .  
  
     ![Incluir el cuadro de diálogo directorios](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Elija la **Macros >>** botón y desplácese hacia abajo en la lista de macros hasta las macros del SDK de Windows para ver los nuevos valores.  
  
     ![Windows SDK Macros](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  Repita este procedimiento con los demás proyectos si es necesario y vuelva a compilar la solución.  
  
### <a name="to-target-the-windows-81-sdk"></a>Para elegir como destino el SDK de Windows 8.1  
  
1.  Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.  
  
2.  En el **versión de la plataforma de destino** lista desplegable, elija **8.1**.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones de escritorio de Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)