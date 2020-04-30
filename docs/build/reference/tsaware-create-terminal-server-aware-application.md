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
ms.openlocfilehash: 0b3fa8bcfd973949e73fdf701db2adb6c58be687
ms.sourcegitcommit: 2f9ff2041d70c406df76c5053151192aad3937ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587383"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Crear una aplicación que reconozca Terminal Server)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Observaciones

La opción/TSAWARE establece una marca en el campo IMAGE_OPTIONAL_HEADER DllCharacteristics en el encabezado opcional de la imagen del programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.

Cuando una aplicación no es Terminal Server consciente (también conocida como aplicación heredada), Terminal Server realiza ciertas modificaciones en la aplicación heredada para que funcione correctamente en un entorno multiusuario. Por ejemplo, Terminal Server creará una carpeta de Windows virtual, de modo que cada usuario obtenga una carpeta de Windows en lugar de obtener el directorio de Windows del sistema. Esto proporciona a los usuarios acceso a sus propios archivos INI. Además, Terminal Server realiza algunos ajustes en el registro para una aplicación heredada. Estas modificaciones ralentizan la carga de la aplicación heredada en Terminal Server.

Si una aplicación es Terminal Server consciente, no debe basarse en archivos INI ni escribir en el registro de **HKEY_CURRENT_USER** durante la instalación.

Si usa/TSAWARE y la aplicación todavía usa archivos INI, todos los usuarios del sistema compartirán los archivos. Si es aceptable, puede vincular la aplicación con/TSAWARE; en caso contrario, debe usar/TSAWARE: NO.

La opción/TSAWARE está habilitada de forma predeterminada para las aplicaciones de Windows y de consola. Consulte [/Subsystem](subsystem-specify-subsystem.md) y [/version](version-version-information.md) para obtener información.

/TSAWARE no es válida para los controladores o archivos dll.

Si una aplicación se vinculó con/TSAWARE, DUMPBIN [/headers](headers.md) mostrará información al efecto.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **Enlazador**.

1. Haga clic en la página de propiedades **sistema** .

1. Modifique la propiedad **Terminal Server** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)<br/>
[Almacenar información específica del usuario](/windows/win32/TermServ/storing-user-specific-information)<br/>
[Aplicaciones heredadas en un entorno de Terminal Services](https://msdn.microsoft.com/library/aa382957.aspx)
