---
title: -SUBSYSTEM | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c12df1a2166c9ef5a1af8a33a5764a8899909edb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377628"
---
# <a name="subsystem"></a>/SUBSYSTEM
Especifica el entorno de ejecución que la imagen ejecutable requiere.  
  
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|  
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción edita la imagen para indicar a qué subsistema debe invocar el sistema operativo para su ejecución.  
  
 Puede especificar uno de los siguientes subsistemas:  
  
 BOOT_APPLICATION  
 Aplicación que se ejecuta en el entorno de arranque de Windows. Para obtener más información acerca de las aplicaciones de arranque, consulte [sobre el proveedor WMI de BCD](http://msdn.microsoft.com/library/aa362639.aspx).  
  
 CONSOLE  
 Una aplicación de modo de carácter de Windows. El sistema operativo proporciona una consola para las aplicaciones de consola.  
  
 Imagen de Extensible Firmware Interface (EFI)  
 Las opciones de subsistema EFI describen imágenes ejecutables que se ejecutan en el entorno de Extensible Firmware Interface. Este entorno se suele proporcionar con el hardware y se ejecuta antes de que el sistema operativo se cargue. Las principales diferencias entre los tipos de imagen EFI son la ubicación de la memoria en la que la imagen se carga y la acción que se realiza cuando se devuelve la llamada a la imagen. Una imagen EFI_APPLICATION se descarga cuando se devuelve el control. Una imagen EFI_BOOT_SERVICE_DRIVER o EFI_RUNTIME_DRIVER se descarga solo si el control regresa con un código de error. Una imagen EFI_ROM se ejecuta desde la memoria ROM. Para obtener más información, vea las especificaciones en el [foro de EFI unificado](http://www.uefi.org/) sitio Web.  
  
 NATIVE  
 Código que se ejecuta sin un entorno de subsistemas, por ejemplo, controladores de dispositivo en modo kernel y procesos del sistema nativos. Esta opción se reserva normalmente para las características del sistema operativo Windows.  
  
 POSIX  
 Aplicación que se ejecuta en el subsistema POSIX en Windows.  
  
 WINDOWS  
 Aplicación que se ejecuta en el entorno gráfico de Windows. Esto incluye aplicaciones de escritorio y aplicaciones de la plataforma Universal de Windows (UWP).  
  
 WINDOWSCE  
 El subsistema WINDOWSCE indica que la aplicación está diseñada para ejecutarse en un dispositivo que tiene una versión del kernel de Windows CE. Las versiones del kernel son PocketPC, Windows Mobile, Windows Phone 7, Windows CE V1.0-6.0R3 y Windows Embedded Compact 7.  
  
 Los valores opcionales `major` y `minor` especifican la versión mínima necesaria del subsistema especificado:  
  
-   La parte de número entero del número de versión (la parte a la izquierda del separador decimal) se representa mediante `major`.  
  
-   La parte fraccionaria del número de versión (la parte a la derecha del separador decimal) se representa mediante `minor`.  
  
-   Los valores de `major` y `minor` deben oscilar entre 0 y 65.535.  
  
 La opción de subsistema afecta a la dirección de inicio predeterminada del programa. Para obtener más información, consulte [/ENTRY (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md), el vinculador/ENTRY:*función* opción.  
  
 Para obtener más información, incluidos los valores mínimo y predeterminado de los números de versión principal y secundaria para cada subsistema, vea el [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opción del vinculador.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)