---
title: -DEBUGTYPE (opciones de información de depuración) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66868f7648d20b890f3c1e8c40802d77e3af4544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375375"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (Opciones de información de depuración)
La opción /DEBUGTYPE especifica los tipos de información de depuración generados por la opción /DEBUG.  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## <a name="arguments"></a>Argumentos  
 CV  
 Indica al enlazador que emita la información de depuración de símbolos, números de línea y demás información de compilación de objetos en el archivo PDB. De forma predeterminada, esta opción está habilitada cuando **/DEBUG** se especifica y **/DEBUGTYPE** no se ha especificado.  
  
 PDATA  
 Indica al enlazador que agregue entradas .pdata y .xdata a la información de flujo de depuración en el archivo PDB. De forma predeterminada, esta opción está habilitada cuando tanto el **/DEBUG** y **Driver/Driver** se especifican opciones. Si **/DEBUGTYPE:PDATA** se especifica por sí mismo, el enlazador incluye automáticamente símbolos de depuración en el archivo PDB. Si **/DEBUGTYPE:PDATA, corrección** se especifica, el vinculador no incluye símbolos de depuración en el archivo PDB.  
  
 FIXUP  
 Indica al enlazador que agregue entradas de la tabla de reubicación a la información de flujo de depuración en el archivo PDB. De forma predeterminada, esta opción está habilitada cuando tanto el **/DEBUG** y **/PROFILE** se especifican opciones. Si **/DEBUGTYPE:FIXUP** o **/DEBUGTYPE:FIXUP, PDATA** se especifica, el vinculador no incluye símbolos de depuración en el archivo PDB.  
  
 Argumentos de **/DEBUGTYPE** se pueden combinar en cualquier orden separándolos con una coma. El **/DEBUGTYPE** opción y sus argumentos no distinguen entre mayúsculas y minúsculas.  
  
## <a name="remarks"></a>Comentarios  
 Use la **/DEBUGTYPE** opción para especificar la inclusión de información de encabezado de datos o .pdata y .xdata para la tabla de reubicación en el flujo de depuración. Esto hace que el enlazador incluya información sobre el código de modo de usuario que está visible en un depurador de kernel cuando se produce una interrupción en el código en modo kernel. Para hacer que los símbolos de depuración estén disponibles cuando **corrección** está especificado, incluya el **CV** argumento.  
  
 Para depurar código en modo de usuario, que es típico para las aplicaciones, el **/DEBUGTYPE** opción no es necesaria. De forma predeterminada, los modificadores de compilador que especifican la depuración de salida ([/Z7, / Zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) emitir todo la información necesaria de Visual Studio del depurador. Use **/DEBUGTYPE:PDATA** o **/DEBUGTYPE:CV, PDATA, corrección** para depurar el código que combine componentes de modo usuario y modo de kernel, como una aplicación de configuración para un controlador de dispositivo. Para obtener más información sobre los depuradores de modo kernel, vea [herramientas de depuración para Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## <a name="see-also"></a>Vea también  
 [/Debug (generar información de depuración)](../../build/reference/debug-generate-debug-info.md)   
 [/Driver (controlador de modo Kernel de Windows NT)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [/Profile (generador de perfiles de herramientas de rendimiento)](../../build/reference/profile-performance-tools-profiler.md)   
 [Herramientas de depuración para Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)