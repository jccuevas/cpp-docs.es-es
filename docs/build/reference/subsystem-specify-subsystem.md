---
title: /SUBSYSTEM (Especificar subsistema)
ms.date: 11/04/2016
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
ms.openlocfilehash: ecda3443d0422af4d5ceec9282d86590c53af2f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821270"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Especificar subsistema)

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>Argumentos

**BOOT_APPLICATION**<br/>
Aplicación que se ejecuta en el entorno de arranque de Windows. Para obtener más información acerca de las aplicaciones de arranque, consulte [sobre BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**CONSOLA DE**<br/>
Aplicación de modo de caracteres Win32. El sistema operativo proporciona una consola para las aplicaciones de consola. Si se define `main` o `wmain` para código nativo, se define `int main(array<String ^> ^)` para código administrado o la aplicación se compila por completo mediante `/clr:safe`, CONSOLE es el valor predeterminado.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Los subsistemas de Extensible Firmware Interface. Para obtener más información, vea la especificación EFI. Para obtener ejemplos, vea el sitio Web de Intel. La versión mínima y la versión predeterminada es 1.0.

**NATIVO**<br/>
Controladores de modo kernel para Windows NT. Esta opción se reserva normalmente para los componentes del sistema operativo Windows. Si [/Driver: WDM](driver-windows-nt-kernel-mode-driver.md) se especifica, nativo es el valor predeterminado.

**POSIX**<br/>
Aplicación que se ejecuta con el subsistema POSIX en Windows NT.

**WINDOWS**<br/>
La aplicación no requiere una consola, probablemente porque crea sus propias ventanas de interacción con el usuario. Si se define `WinMain` o `wWinMain` para código nativo o se define `WinMain(HISTANCE *, HINSTANCE *, char *, int)` o `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` para código administrado, WINDOWS es el valor predeterminado.

*principales* y *secundaria*<br/>
(Opcional) Especifique la versión mínima requerida del subsistema. Los argumentos son números decimales comprendidos en el intervalo de 0 a 65.535. Vea la sección Comentarios para obtener más información. No existen límites superiores para los números de versión.

## <a name="remarks"></a>Comentarios

El **/Subsystem** opción especifica el entorno del ejecutable.

La opción de subsistema afecta al símbolo de punto de entrada (o función de punto de entrada) que el vinculador seleccionará.

El mínimo opcional y el valor predeterminado *principales* y *menores* números de versión de los subsistemas son los siguientes.

|Subsistema|Mínima|Default|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|CONSOLE|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|WINDOWS|5.01 (x 86) 5.02 (x 64) 6.02 (ARM)|6.00 (x86, x64) 6.02 (ARM)|
|NATIVE (con DRIVER:WDM)|1.00 (x86) 1.10 (x64, ARM)|1.00 (x86) 1.10 (x64, ARM)|
|NATIVE (sin /DRIVER:WDM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|4.00 (x 86) 5.02 (x 64) 6.02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione la carpeta Vinculador.

1. Seleccione el **sistema** página de propiedades.

1. Modifique la propiedad `SubSystem`.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
