---
title: -SUBSYSTEM (Especificar subsistema) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs: C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fd96a89ef4228835307f8f8f0d9fff5d61441f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (Especificar subsistema)
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 Aplicación que se ejecuta en el entorno de arranque de Windows. Para obtener más información acerca de las aplicaciones de arranque, consulte [acerca de BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639).  
  
 CONSOLE  
 Aplicación de modo de caracteres Win32. El sistema operativo proporciona una consola para las aplicaciones de consola. Si se define `main` o `wmain` para código nativo, se define `int main(array<String ^> ^)` para código administrado o la aplicación se compila por completo mediante `/clr:safe`, CONSOLE es el valor predeterminado.  
  
 Interfaz de firmware extensible (EFI)  
 Los subsistemas EFI_*. Para obtener más información, vea la especificación EFI. Para ver un ejemplo, visite el sitio web de Intel. La versión mínima y la versión predeterminada es 1.0.  
  
 NATIVE  
 Controladores de modo kernel para Windows NT. Esta opción se reserva normalmente para los componentes del sistema operativo Windows. Si [/Driver: WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md) se especifica, nativo es el valor predeterminado.  
  
 POSIX  
 Aplicación que se ejecuta con el subsistema POSIX en Windows NT.  
  
 WINDOWS  
 La aplicación no requiere una consola, probablemente porque crea sus propias ventanas de interacción con el usuario. Si se define `WinMain` o `wWinMain` para código nativo o se define `WinMain(HISTANCE *, HINSTANCE *, char *, int)` o `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)` para código administrado, WINDOWS es el valor predeterminado.  
  
 `Major` y `minor` (opcional)  
 Especifique la versión mínima requerida del subsistema. Los argumentos son números decimales comprendidos en el intervalo de 0 a 65.535. Vea la sección Comentarios para obtener más información. No existen límites superiores para los números de versión.  
  
## <a name="remarks"></a>Comentarios  
 La opción /SUBSYSTEM especifica el entorno del ejecutable.  
  
 La opción de subsistema afecta al símbolo de punto de entrada (o función de punto de entrada) que el vinculador seleccionará.  
  
 Los números opcionales de versión `major` y `minor` mínima y predeterminada de los subsistemas son los siguientes.  
  
|Subsistema|Mínima|Default|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|CONSOLE|5.01 (x86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6.00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|WINDOWS|5.01 (x86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6.00 (x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|NATIVE (con DRIVER:WDM)|1.00 (x86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|1.00 (x86) 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM)|  
|NATIVE (sin /DRIVER:WDM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|4.00 (x 86) 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION, EFI_BOOT_SERVICE_DRIVER, EFI_ROM, EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta Vinculador.  
  
3.  Seleccione el **System** página de propiedades.  
  
4.  Modifique la propiedad `SubSystem`.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)