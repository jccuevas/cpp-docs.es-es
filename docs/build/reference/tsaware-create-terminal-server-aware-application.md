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
ms.openlocfilehash: fe31763c5da21a724f0c9242e6eb8429a2379ecd
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421505"
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

La opción /TSAWARE está habilitada de forma predeterminada para Windows y aplicaciones de consola. Consulte [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) y [/VERSION](../../build/reference/version-version-information.md) para obtener información.

/ TSAWARE no es válido para los controladores, vxd o DLL.

Si una aplicación se vinculó TSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) mostrará información al respecto.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modificar el **Terminal Server** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[Almacenar información específica del usuario](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Aplicaciones heredadas en un entorno de servicios de Terminal Server](https://msdn.microsoft.com/library/aa382957.aspx)
