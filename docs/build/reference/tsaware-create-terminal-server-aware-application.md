---
title: /TSAWARE (Crear una aplicación que reconozca Terminal Server)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: f6ed6184f8ae4b3a0f9db3c1f962a2918a185138
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317437"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Crear una aplicación que reconozca Terminal Server)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Comentarios

La opción /TSAWARE establece una marca en el campo IMAGE_OPTIONAL_HEADER DllCharacteristics del encabezado opcional de la imagen programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.

Cuando una aplicación no es consciente de Terminal Server (también conocido como una aplicación heredada), Terminal Server realiza ciertas modificaciones en la aplicación heredada para que funcione correctamente en un entorno multiusuario. Por ejemplo, Terminal Server creará una carpeta virtual de Windows, tal que cada usuario obtenga una carpeta de Windows en lugar de obtener el directorio del sistema Windows. Esto proporciona a los usuarios acceso a sus propios archivos INI. Además, Terminal Server realiza algunos ajustes en el registro para una aplicación heredada. Estos se ralentiza la carga de la aplicación heredada en Terminal Server.

Si una aplicación está preparada para Terminal Server, no debe depender de archivos INI ni escribir en el **HKEY_CURRENT_USER** registro durante la instalación.

Si usa /TSAWARE y la aplicación todavía utiliza archivos INI, se compartirá los archivos de todos los usuarios del sistema. Si es aceptable, todavía puede vincular la aplicación/TSAWARE; en caso contrario, deberá usar/TSAWARE: no.

La opción /TSAWARE está habilitada de forma predeterminada para Windows y aplicaciones de consola. Consulte [/Subsystem](subsystem-specify-subsystem.md) y [/VERSION](version-version-information.md) para obtener información.

/ TSAWARE no es válido para los controladores, vxd o DLL.

Si una aplicación se vinculó TSAWARE, DUMPBIN [/HEADERS](headers.md) mostrará información al respecto.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modificar el **Terminal Server** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[Almacenar información específica del usuario](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Aplicaciones heredadas en un entorno de servicios de Terminal Server](https://msdn.microsoft.com/library/aa382957.aspx)
