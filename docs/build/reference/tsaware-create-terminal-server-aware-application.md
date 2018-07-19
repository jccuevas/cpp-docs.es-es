---
title: -TSAWARE (Crear aplicación compatible con servicios de Terminal Server) | Documentos de Microsoft
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
ms.openlocfilehash: e386c9024ea7736adb2766488c1c51c80ff7177b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379138"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Crear una aplicación que reconozca Terminal Server)
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /TSAWARE establece una marca en el campo IMAGE_OPTIONAL_HEADER DllCharacteristics del encabezado opcional de la imagen programa. Si se establece esta marca, Terminal Server no realizará determinados cambios en la aplicación.  
  
 Cuando una aplicación no está preparada para Terminal Server (también conocido como una aplicación heredada), Terminal Server hace que ciertas modificaciones a la aplicación heredada para que funcione correctamente en un entorno multiusuario. Por ejemplo, Terminal Server creará una carpeta virtual de Windows, por ejemplo, que cada usuario obtenga una carpeta de Windows en lugar de obtener el directorio del sistema Windows. Esto proporciona a los usuarios acceso a sus propios archivos INI. Además, Terminal Server realiza algunos ajustes en el registro de la aplicación heredada. Estos se ralentiza la carga de la aplicación heredada en Terminal Server.  
  
 Si una aplicación está preparada para Terminal Server, no debe confiar en los archivos INI ni escribir en el **HKEY_CURRENT_USER** registro durante la instalación.  
  
 Si se usa /TSAWARE y la aplicación todavía utiliza archivos INI, se compartirá los archivos de todos los usuarios del sistema. Si es aceptable, aún puede vincular la aplicación/TSAWARE; en caso contrario, debe usar/TSAWARE: no.  
  
 La opción /TSAWARE está habilitada de forma predeterminada para Windows y aplicaciones de consola. Vea [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) y [/VERSION](../../build/reference/version-version-information.md) para obtener información.  
  
 /TSAWARE no es válida para controladores, vxd o DLL.  
  
 Si se vincula una aplicación de/TSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) mostrará información al respecto.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **System** página de propiedades.  
  
4.  Modificar el **Terminal Server** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Almacenar información específica del usuario](http://msdn.microsoft.com/library/aa383452)   
 [Aplicaciones heredadas en un entorno de servicios de Terminal Server](https://msdn.microsoft.com/en-us/library/aa382957.aspx)