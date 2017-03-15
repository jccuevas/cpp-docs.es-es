---
title: "/DEBUGTYPE (Opciones de informaci&#243;n de depuraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/debugtype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Opción del enlazador /DEBUGTYPE"
  - "Opción del enlazador DEBUGTYPE"
  - "Opción del enlazador -DEBUGTYPE"
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# /DEBUGTYPE (Opciones de informaci&#243;n de depuraci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción \/DEBUGTYPE especifica los tipos de información de depuración generados por la opción \/DEBUG.  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## Argumentos  
 CV  
 Indica al enlazador que emita la información de depuración de símbolos, números de línea y demás información de compilación de objetos en el archivo PDB.  De forma predeterminada, esta opción está habilitada cuando se especifica **\/DEBUG** y **\/DEBUGTYPE** no se ha especificado.  
  
 PDATA  
 Indica al enlazador que agregue entradas .pdata y .xdata a la información de flujo de depuración en el archivo PDB.  Esta opción está habilitada de forma predeterminada si se han especificado las opciones **\/DEBUG** y **\/DRIVER**.  Si **\/DEBUGTYPE:PDATA** se especifica por sí misma, el enlazador incluye automáticamente símbolos de depuración en el archivo PDB.  Si **\/DEBUGTYPE:PDATA,FIXUP** se especifica por sí misma, el enlazador no incluye símbolos de depuración en el archivo PDB.  
  
 FIXUP  
 Indica al enlazador que agregue entradas de la tabla de reubicación a la información de flujo de depuración en el archivo PDB.  Esta opción está habilitada de forma predeterminada si se han especificado las opciones **\/DEBUG** y **\/PROFILE**.  Si se especifica **\/DEBUGTYPE:FIXUP** o **\/DEBUGTYPE:FIXUP,PDATA**, el enlazador no incluye símbolos de depuración en el archivo PDB.  
  
 Los argumentos de **\/DEBUGTYPE** se pueden combinar en cualquier orden separándolos mediante una coma.  La opción **\/DEBUGTYPE** y sus argumentos no distinguen mayúsculas de minúsculas.  
  
## Comentarios  
 Use la opción **\/DEBUGTYPE** para especificar la inclusión de datos de la tabla de reubicación o información de encabezado .pdata y .xdata en el flujo de depuración.  Esto hace que el enlazador incluya información sobre el código de modo de usuario que está visible en un depurador de kernel cuando se produce una interrupción en el código en modo kernel.  Para hacer que los símbolos de depuración estén disponibles cuando se especifica **FIXUP**, incluya el argumento **CV**.  
  
 Para depurar el código en modo de usuario, que es típico en el caso de las aplicaciones, no se necesita la opción **\/DEBUGTYPE**.  De forma predeterminada, los modificadores del compilador que especifican la salida de depuración \([\/Z7, \/Zi, \/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)\) emiten toda la información que necesita el depurador de Visual Studio.  Use **\/DEBUGTYPE:PDATA** o **\/DEBUGTYPE:CV,PDATA,FIXUP** para depurar código que combine componentes de modo usuario y de modo kernel, como es el caso de una aplicación de configuración para un controlador de dispositivo.  Para obtener más información sobre los depuradores de modo kernel, vea [Herramientas de depuración para Windows \(WinDbg, KD, CDB, NTSD\)](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## Vea también  
 [\/DEBUG \(Generar información de depuración\)](../../build/reference/debug-generate-debug-info.md)   
 [\/DRIVER \(Controlador de modo kernel de Windows NT\)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [\/PROFILE \(Generador de perfiles de Herramientas de rendimiento\)](../../build/reference/profile-performance-tools-profiler.md)   
 [Herramientas de depuración para Windows \(WinDbg, KD, CDB, NTSD\)](http://go.microsoft.com/fwlink/p?LinkID=285651)