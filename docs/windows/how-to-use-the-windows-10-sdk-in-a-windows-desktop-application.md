---
title: "Procedimiento de uso del SDK de Windows 10 en una aplicaci&#243;n de escritorio de Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedimiento de uso del SDK de Windows 10 en una aplicaci&#243;n de escritorio de Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea un proyecto de escritorio de Windows clásico en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], se configura de forma predeterminada para que use el SDK de Windows 8.1 para compilar. Esta versión del SDK de Windows es compatible con todas las versiones recientes de Windows, incluida Windows 10, pero no contiene las funciones de CRT ni las API de Windows 10 más recientes que se encuentran en el SDK de Windows 10. Si quiere usar las nuevas API, puede redestinar el proyecto para que haga referencia al SDK de Windows 10.  
  
 A partir de [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] y el SDK de Windows 10, la biblioteca de CRT se divide en dos partes: una \(ucrtbase\) que contiene las funciones que se pueden usar en las aplicaciones universales de Windows y otra que contiene todo lo demás \(vcruntime140\). Puesto que el SDK de Windows 10 contiene nuevas funciones como, por ejemplo, muchas funciones de C99, tendrá que seguir estos pasos para usar esas funciones. Vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
### Para elegir como destino el SDK de Windows 10  
  
1.  Asegúrese de que esté instalado el SDK de Windows 10. El SDK de Windows 10 se instala como parte de las [Herramientas de desarrollo de Windows 10](http://go.microsoft.com/fwlink/?LinkID=617631).  
  
2.  Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.  
  
     ![Redestinar versión de SDK](../windows/media/retargetingwindowssdk1.png "RetargetingWindowsSDK1")  
  
     Se mostrará el diálogo **Revisar acciones de solución**.  
  
     ![Revisar acciones de solución](../windows/media/retargetingwindowssdk2.png "RetargetingWindowsSDK2")  
  
3.  En la lista desplegable **Versión de la plataforma de destino**, elija la versión del SDK de Windows 10 que desee establecer como destino, o elija 8.1 si no quiere realizar ningún cambio. Elija el botón Aceptar para aplicar el cambio.  
  
     Tenga en cuenta que 8.1, en este contexto, hace referencia a la versión del SDK de Windows, que también es compatible con Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 y Windows Vista.  
  
     Si este paso se realiza correctamente, aparecerá el siguiente texto en la ventana de salida:  
  
     `Redestinando extremo: 1 completado, 0 dio error, 0 omitido`  
  
4.  Abra las propiedades del proyecto y, en la sección **Propiedades de configuración, General**, observe los valores de **Versión de plataforma de destino de Windows**. Cambiar el valor aquí tiene el mismo efecto que seguir este procedimiento. Vea [Página de propiedades General \(Proyecto\)](../ide/general-property-page-project.md).  
  
     ![Versión de la plataforma de destino](../windows/media/retargetingwindowssdk3.png "RetargetingWindowsSDK3")  
  
     Esta acción cambia los valores de las macros del proyecto que incluyen rutas de acceso a archivos de encabezado y archivos de biblioteca. Para ver qué cambió, en la sección Directorios de Visual C\+\+ del diálogo Propiedades del proyecto, elija una de las propiedades, como Directorios de archivos de inclusión, elija la opción de abrir la lista desplegable y elija \<Editar\>. Se mostrará el diálogo **Directorios de archivos de inclusión**.  
  
     ![Cuadro de diálogo Incluir directorios](../windows/media/retargetingwindowssdk4.png "RetargetingWindowsSDK4")  
  
     Elija el botón **Macros \>\>** y desplácese hacia abajo por la lista de macros hasta las macros del SDK de Windows para ver todos los nuevos valores.  
  
     ![Macros de Windows SDK](../windows/media/retargetingwindowssdk5.png "RetargetingWindowsSDK5")  
  
5.  Repita este procedimiento con los demás proyectos si es necesario y vuelva a compilar la solución.  
  
### Para elegir como destino el SDK de Windows 8.1  
  
1.  Abra el menú contextual del nodo del proyecto y elija **Redestinar versión de SDK**.  
  
2.  En la lista desplegable Versión de la plataforma de destino, elija 8.1.  
  
## Vea también  
 [Windows Desktop Applications \(Visual C\+\+\)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)