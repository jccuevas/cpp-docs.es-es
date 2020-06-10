---
title: 'Controles ActiveX de MFC: distribuir controles ActiveX'
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
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
ms.openlocfilehash: 11d647922a4f8097e03e112c0c93c833524c2c4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618201"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Controles ActiveX de MFC: distribuir controles ActiveX

En este artículo se describen varios problemas relacionados con la redistribución de controles ActiveX:

- [Versiones de controles ANSI o Unicode](#_core_ansi_or_unicode_control_versions)

- [Instalar controles ActiveX y archivos dll redistribuibles](#_core_installing_activex_controls_and_redistributable_dlls)

- [Registrar controles](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>Versiones de controles ANSI o Unicode

Debe decidir si desea enviar una versión ANSI o Unicode del control, o ambos. Esta decisión se basa en factores de portabilidad inherentes en los juegos de caracteres ANSI y Unicode.

Los controles ANSI, que funcionan en todos los sistemas operativos Win32, permiten obtener la máxima portabilidad entre los distintos sistemas operativos Win32. Los controles Unicode solo funcionan en Windows NT (versión 3,51 o posterior), pero no en Windows 95 o Windows 98. Si la portabilidad es su principal preocupación, envíe controles ANSI. Si los controles solo se ejecutan en Windows NT, puede enviar controles Unicode. También puede optar por enviar y hacer que la aplicación Instale la versión más adecuada para el sistema operativo del usuario.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Instalar controles ActiveX y archivos dll redistribuibles

El programa de instalación que se proporciona con los controles ActiveX debe crear un subdirectorio especial del directorio de Windows e instalar los controles. Archivos OCX.

> [!NOTE]
> Use la `GetWindowsDirectory` API de Windows en el programa de instalación para obtener el nombre del directorio de Windows. Puede que desee obtener el nombre del subdirectorio del nombre de la empresa o del producto.

El programa de instalación debe instalar los archivos DLL redistribuibles necesarios en el directorio del sistema de Windows. Si alguno de los archivos DLL ya está presente en el equipo del usuario, el programa de instalación debe comparar sus versiones con las versiones que está instalando. Reinstale un archivo solo si su número de versión es mayor que el archivo ya instalado.

Dado que los controles ActiveX solo se pueden usar en aplicaciones de contenedor OLE, no es necesario distribuir el conjunto completo de archivos dll OLE con los controles. Puede suponer que la aplicación contenedora (o el propio sistema operativo) tiene instaladas las DLL estándar de OLE.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Registrar controles

Para poder usar un control, se deben crear entradas adecuadas en la base de datos de registro de Windows. Algunos contenedores de controles ActiveX proporcionan un elemento de menú para que los usuarios registren nuevos controles, pero es posible que esta característica no esté disponible en todos los contenedores. Por lo tanto, puede que desee que el programa de instalación registre los controles cuando se instalan.

Si lo prefiere, puede escribir el programa de instalación para registrar el control directamente en su lugar.

Use la `LoadLibrary` API de Windows para cargar el archivo dll de control. A continuación, use `GetProcAddress` para obtener la dirección de la función "DllRegisterServer". Por último, llame a la `DllRegisterServer` función. En el ejemplo de código siguiente se muestra un método posible, donde `hLib` almacena el identificador de la biblioteca de controles y `lpDllEntryPoint` almacena la dirección de la función "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

La ventaja de registrar el control directamente es que no es necesario invocar y cargar un proceso independiente (es decir, REGSVR32), lo que reduce el tiempo de instalación. Además, dado que el registro es un proceso interno, el programa de instalación puede controlar errores y situaciones imprevistas mejor que un proceso externo.

> [!NOTE]
> Antes de que el programa de instalación Instale un control ActiveX, debe llamar a `OleInitialize` . Una vez finalizado el programa de instalación, llame a `OleUnitialize` . Esto garantiza que los archivos DLL del sistema OLE están en el estado adecuado para registrar un control ActiveX.

Debe registrar MFCx0. DLL.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
