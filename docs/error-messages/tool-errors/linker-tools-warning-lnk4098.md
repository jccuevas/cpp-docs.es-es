---
title: Las herramientas del vinculador LNK4098 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b199c19417d7d3be866109fff7361fb4ead959d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4098"></a>Advertencia de las herramientas del vinculador LNK4098
DEFAULTLIB entra en conflicto 'library' con el uso de otras bibliotecas; Use/NODEFAULTLIB: biblioteca  
  
 Está intentando vincular con bibliotecas incompatibles.  
  
> [!NOTE]
>  Las bibliotecas en tiempo de ejecución contienen ahora directivas para impedir que se mezclen tipos diferentes. Recibirá esta advertencia si se intenta usar diferentes tipos o depurar no son versiones de depuración y de la biblioteca en tiempo de ejecución en el mismo programa. Por ejemplo, si compila un archivo para utilizar una biblioteca de tipo de tiempo de ejecución y otro archivo para que utilice otro tipo (por ejemplo, único subproceso y multiproceso) e intentaron vincularlos, aparecerá esta advertencia. Debe compilar todos los archivos de origen para utilizar la misma biblioteca de tiempo de ejecución. Consulte la [utilizar la biblioteca en tiempo de ejecución](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) opciones del compilador para obtener más información.  
  
 Puede utilizar el vinculador [/verbose: lib](../../build/reference/verbose-print-progress-messages.md) conmutador para determinar en qué bibliotecas busca el vinculador. Si recibes LNK4098 y desea crear un archivo ejecutable que usa, por ejemplo, el único subproceso, no son de depuración bibliotecas en tiempo de ejecución, use la **/verbose: lib** opción para averiguar qué bibliotecas busca el vinculador. El vinculador debe mostrar LIBC.lib y no LIBCMT.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib o MSVCRTD.lib como bibliotecas de su búsqueda. Puede indicar al vinculador que omita las bibliotecas en tiempo de ejecución incorrectas mediante [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) para cada biblioteca que desea omitir.  
  
 La siguiente tabla muestra qué bibliotecas deben omitirse según qué biblioteca en tiempo de ejecución que desea usar.  
  
|Para usar esta biblioteca en tiempo de ejecución|Pasar por alto estas bibliotecas|  
|-----------------------------------|----------------------------|  
|Un único subproceso (libc.lib)|LIBCMT.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Multiproceso (libcmt.lib)|libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Multiproceso con DLL (msvcrt.lib)|libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Un único subproceso de depuración (libcd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, msvcrtd.lib|  
|Depuración multiproceso (libcmtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, msvcrtd.lib|  
|Depuración multiproceso con DLL (msvcrtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|  
  
 Por ejemplo, si ha recibido esta advertencia y desea crear un archivo ejecutable que utiliza la versión no son de depuración y un único subproceso de las bibliotecas en tiempo de ejecución, podría utilizar las siguientes opciones con el vinculador:  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```