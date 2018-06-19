---
title: 'Controles ActiveX MFC: Distribuir controles ActiveX | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6658c972b9d9cdeececd43a89ac424964d2289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358812"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Controles ActiveX de MFC: distribuir controles ActiveX
En este artículo se describe varios problemas relacionados con la redistribución de controles ActiveX:  
  
-   [Versiones ANSI o Unicode de un Control](#_core_ansi_or_unicode_control_versions)  
  
-   [Instalar controles ActiveX y archivos DLL redistribuibles](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [Registrar controles](#_core_registering_controls)  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> Versiones ANSI o Unicode de un Control  
 Debe decidir si va a suministrar una versión ANSI o Unicode del control, o ambos. Esta decisión se basa en factores de portabilidad inherentes en juegos de caracteres ANSI y Unicode.  
  
 Los controles ANSI, que funcionan en todos los sistemas operativos de Win32, se permiten para la máxima portabilidad entre los distintos sistemas operativos de Win32. Los controles de Unicode funcionan en Windows NT (versión 3.51 o versiones posterior), pero no en Windows 95 o Windows 98. Si la portabilidad es la principal preocupación, suministre controles ANSI. Si los controles se ejecutarán solo en Windows NT, puede suministrar controles Unicode. También puede optar por suministrar ambos y hacer que la aplicación se instale la versión más adecuada para el sistema operativo del usuario.  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Instalar controles ActiveX y archivos DLL redistribuibles  
 El programa de instalación que se proporcionan con los controles ActiveX debería crear un subdirectorio especial al directorio de Windows e instalar los controles. Archivos OCX en ella.  
  
> [!NOTE]
>  Utilizar las ventanas de **GetWindowsDirectory** API en el programa de instalación para obtener el nombre del directorio de Windows. Puede que desee para el nombre del subdirectorio se deriva el nombre de su empresa o producto.  
  
 El programa de instalación debe instalar los archivos DLL redistribuibles necesarios en el directorio de sistema de Windows. Si cualquiera de los archivos DLL ya están presente en el equipo del usuario, el programa de instalación debería comparar su versión con las versiones que se va a instalar. Vuelva a instalar un archivo sólo si su número de versión es mayor que el archivo ya instalado.  
  
 Dado que los controles ActiveX se pueden utilizar sólo en aplicaciones de contenedor OLE, no es necesario para distribuir el conjunto completo de las DLL OLE con los controles. Se puede asumir que la aplicación contenedora (o el propio sistema operativo) tiene los archivos DLL de OLE instalados.  
  
##  <a name="_core_registering_controls"></a> Registrar controles  
 Para poder usar un control, deben crearse entradas adecuadas para él en la base de datos de registro de Windows. Algunos contenedores de controles ActiveX proporcionan un elemento de menú para que los usuarios registren nuevos controles, pero esta característica no esté disponible en todos los contenedores. Por lo tanto, puede que el programa de instalación para registrar los controles cuando se instalan.  
  
 Si lo prefiere, puede escribir el programa de instalación para registrar el control directamente en su lugar.  
  
 Use la **LoadLibrary** API de Windows para cargar la DLL del control. A continuación, use **GetProcAddress** para obtener la dirección de la función "DllRegisterServer". Por último, llame a la `DllRegisterServer` (función). El ejemplo de código siguiente muestra un método posible, donde `hLib` almacena el identificador de la biblioteca de controles, y `lpDllEntryPoint` almacena la dirección de la función "DllRegisterServer".  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 La ventaja de registrar el control directamente es que no necesite invocar y cargar un proceso independiente (es decir, REGSVR32), lo que reduce el tiempo de instalación. Además, dado que el registro es un proceso interno, el programa de instalación puede controlar errores y situaciones imprevistas mejor que un proceso externo pueden.  
  
> [!NOTE]
>  Antes de que el programa de instalación instale un control ActiveX, debe llamar a **OleInitialize**. Cuando finaliza el programa de instalación, llame a **OleUnitialize**. Esto garantiza que la DLL del sistema OLE están en el estado apropiado para registrar un control ActiveX.  
  
 Debe registrar MFCx0.DLL.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

