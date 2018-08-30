---
title: -TSAWARE (crear la aplicación que reconozca Terminal Server) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs:
- C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9caf6c9a47a667b57220b6bf577080d3548e94e9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198555"
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
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **sistema** página de propiedades.  
  
4.  Modificar el **Terminal Server** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Almacenar información específica del usuario](/windows/desktop/TermServ/storing-user-specific-information)   
 [Aplicaciones heredadas en un entorno de servicios de Terminal Server](https://msdn.microsoft.com/library/aa382957.aspx)