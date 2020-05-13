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
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364625"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Controles ActiveX de MFC: distribuir controles ActiveX

En este artículo se describen varios problemas relacionados con la redistribución de controles ActiveX:

- [Versiones de control ANSI o Unicode](#_core_ansi_or_unicode_control_versions)

- [Instalación de controles ActiveX y archivos DLL redistribuibles](#_core_installing_activex_controls_and_redistributable_dlls)

- [Registro de controles](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>Versiones de control ANSI o Unicode

Debe decidir si desea enviar una versión ANSI o Unicode del control, o ambos. Esta decisión se basa en factores de portabilidad inherentes a los conjuntos de caracteres ANSI y Unicode.

Los controles ANSI, que funcionan en todos los sistemas operativos Win32, permiten la máxima portabilidad entre los distintos sistemas operativos Win32. Los controles Unicode solo funcionan en Windows NT (versión 3.51 o posterior), pero no en Windows 95 o Windows 98. Si la portabilidad es su principal preocupación, envíe los controles ANSI. Si los controles se ejecutarán solo en Windows NT, puede enviar controles Unicode. También puede optar por enviar ambos y hacer que la aplicación instale la versión más adecuada para el sistema operativo del usuario.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Instalación de controles ActiveX y archivos DLL redistribuibles

El programa de instalación que proporcione con los controles ActiveX debe crear un subdirectorio especial del directorio de Windows e instalar los controles». OCX en él.

> [!NOTE]
> Utilice la `GetWindowsDirectory` API de Windows en el programa de instalación para obtener el nombre del directorio de Windows. Es posible que desee derivar el nombre del subdirectorio del nombre de su empresa o producto.

El programa de instalación debe instalar los archivos DLL redistribuibles necesarios en el directorio del sistema de Windows. Si alguno de los archivos DLL ya está presente en el equipo del usuario, el programa de instalación debe comparar sus versiones con las versiones que está instalando. Vuelva a instalar un archivo solo si su número de versión es mayor que el archivo ya instalado.

Dado que los controles ActiveX solo se pueden usar en aplicaciones de contenedor OLE, no es necesario distribuir el conjunto completo de archivos DLL OLE con los controles. Puede suponer que la aplicación contenedora (o el propio sistema operativo) tiene instalados los archivos DLL OLE estándar.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Registro de controles

Antes de que se pueda usar un control, se deben crear entradas adecuadas para él en la base de datos de registro de Windows. Algunos contenedores de controles ActiveX proporcionan un elemento de menú para que los usuarios registren nuevos controles, pero es posible que esta característica no esté disponible en todos los contenedores. Por lo tanto, es posible que desee que el programa de instalación registre los controles cuando se instalan.

Si lo prefiere, puede escribir su programa de instalación para registrar el control directamente en su lugar.

Use `LoadLibrary` la API de Windows para cargar el archivo DLL de control. A continuación, se utiliza `GetProcAddress` para obtener la dirección de la función "DllRegisterServer". Por último, `DllRegisterServer` llame a la función. En el ejemplo de código siguiente `hLib` se muestra un método `lpDllEntryPoint` posible, donde almacena el identificador de la biblioteca de controles y almacena la dirección de la función "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

La ventaja de registrar el control directamente es que no es necesario invocar y cargar un proceso independiente (es decir, REGSVR32), lo que reduce el tiempo de instalación. Además, debido a que el registro es un proceso interno, el programa de instalación puede manejar errores y situaciones imprevistas mejor que un proceso externo.

> [!NOTE]
> Antes de que el programa de instalación `OleInitialize`instale un control ActiveX, debe llamar a . Cuando finalice el programa `OleUnitialize`de instalación, llame a . Esto garantiza que los archivos DLL del sistema OLE están en el estado adecuado para registrar un control ActiveX.

Debe registrar MFCx0.DLL.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
