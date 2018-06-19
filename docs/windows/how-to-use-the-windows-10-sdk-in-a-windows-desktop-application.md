---
title: 'Cómo: utilizar las ventanas de 10 SDK en una aplicación de escritorio de Windows | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 04/19/2018
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
ms.openlocfilehash: 2dae6f31082176c94cdf12cf0cdb42ba13aa93fe
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882829"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Procedimiento de uso del SDK de Windows 10 en una aplicación de escritorio de Windows
Cuando crea un proyecto de escritorio clásico de Windows en Visual Studio de 2017, se configura de forma predeterminada para compilar con la versión del SDK de Windows 10 que estaba instalado cuando se instaló o actualizó por última vez la carga de trabajo de escritorio de C++. Esta versión del SDK de Windows es compatible con todas las versiones recientes de Windows. Si desea tener como destino una versión anterior del SDK, puede abrir proyecto | Propiedades y elija una de las otras versiones del SDK disponibles en la lista desplegable de versión del SDK de Windows.  
  
 A partir de Visual Studio 2015 y el SDK de Windows 10, la biblioteca CRT se divide en dos partes: una (ucrtbase) que contiene las funciones que son aceptables para su uso en aplicaciones universales de Windows y otra que contiene todo lo demás (vcruntime140). Puesto que el SDK de Windows 10 contiene nuevas funciones como, por ejemplo, muchas funciones de C99, tendrá que seguir estos pasos para usar esas funciones. Consulte [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Para elegir como destino el SDK de Windows 10  
  
1.  Asegúrese de que esté instalado el SDK de Windows 10. El SDK de Windows 10 se instala como parte de la **el desarrollo de escritorio con C++** carga de trabajo. Una versión independiente está disponible en [descarga y las herramientas para Windows 10](https://developer.microsoft.com/windows/downloads).

  
2.  Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.  
  
     ![Redestinar versión SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     Se mostrará el diálogo **Revisar acciones de solución** .  
  
     ![Revise las acciones de solución](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  En el **versión de la plataforma de destino** lista desplegable, elija la versión del SDK de Windows 10 que desee cambiar. Elija el botón Aceptar para aplicar el cambio.  
  
     Tenga en cuenta que 8.1, en este contexto, hace referencia a la versión del SDK de Windows, que también es compatible con Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 y Windows Vista.  
  
     Si este paso se realiza correctamente, aparecerá el siguiente texto en la ventana de salida:  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Abra las propiedades del proyecto y, en la sección **Propiedades de configuración, General** , observe los valores de **Versión de plataforma de destino de Windows**. Cambiar el valor aquí tiene el mismo efecto que seguir este procedimiento. Vea [General Property Page (Project)](../ide/general-property-page-project.md).  
  
     ![Versión de la plataforma de destino](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Esta acción cambia los valores de las macros del proyecto que incluyen rutas de acceso a archivos de encabezado y archivos de biblioteca. Para ver qué cambió, en la sección directorios de Visual C++ del cuadro de diálogo Propiedades del proyecto, elija una de las propiedades, como los directorios de inclusión, elija para abrir la lista desplegable y elija \<Editar >. Se mostrará el diálogo **Directorios de archivos de inclusión** .  
  
     ![Incluir el cuadro de diálogo directorios](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Elija la **Macros >>** botón y desplácese hacia abajo en la lista de macros hasta las macros del SDK de Windows para ver todos los nuevos valores.  
  
     ![Macros del SDK de Windows](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  Repita este procedimiento con los demás proyectos si es necesario y vuelva a compilar la solución.  
  
### <a name="to-target-the-windows-81-sdk"></a>Para elegir como destino el SDK de Windows 8.1  
  
1.  Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.  
  
2.  En la lista desplegable Versión de la plataforma de destino, elija 8.1.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones de escritorio de Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
