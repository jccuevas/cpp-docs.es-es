---
title: Compatibilidad con bibliotecas para ensamblados mixtos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b3bc50416eceac64c134a31a4d7384e33db69b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="library-support-for-mixed-assemblies"></a>Compatibilidad con bibliotecas para ensamblados mixtos
Visual C++ admite el uso de la biblioteca estándar de C++, la biblioteca de Common RunTime (CRT), ATL y MFC para aplicaciones compiladas con [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md). Esto permite a las aplicaciones existentes que utilizan estas bibliotecas para utilizar características de .NET Framework también.  
  
 Esta compatibilidad incluye las siguientes nuevas bibliotecas de importación y el archivo DLL:  
  
-   Msvcmrt [d] .lib si se compila con/CLR. Vínculos de ensamblados mixtos a esta biblioteca de importación.  
  
-   Msvcm90 [d] .dll y Msvcurt [d] .lib si se compila con/CLR: pure. El archivo DLL es un ensamblado mixto que proporciona compatibilidad de tiempo de ejecución de C (CRT) administrada y forma parte de un ensamblado administrado instalado en la caché de ensamblados global (GAC). Los ensamblados puros se vinculan a esta biblioteca de importación y terminan enlazados a Msvcm90.dll.  
  
 Esta compatibilidad proporciona que algunas ventajas relacionadas:  
  
-   La biblioteca estándar de C++ y CRT están disponibles para código mixto y puro. CRT y la biblioteca estándar de C++ proporcionadas no son comprobables; en última instancia, las llamadas todavía se enrutan a la misma biblioteca estándar de C++ y CRT usan desde el código nativo.  
  
-   Se corrige el control de excepciones unificado en imágenes puras y mixtas.  
  
-   Inicialización estática de variables de C++ en imágenes puras y mixtas.  
  
-   Compatibilidad con las variables por AppDomain y por proceso en código administrado.  
  
-   Resuelve los problemas de bloqueo del cargador que se aplican a las DLL mixtas compiladas en Visual Studio 2003 y versiones anteriores.  
  
 Además, esta compatibilidad presenta las siguientes limitaciones:  
  
-   Solo el modelo del archivo DLL de CRT es compatible (tanto para código compilado con /clr o/CLR: pure).  
  
-   No se pueden mezclar objetos puros y mixtos en una sola imagen si los objetos usan las bibliotecas de Visual C++ (ya que todos los objetos deben ser puros en una imagen pura). Si lo hace, recibirá errores en tiempo de vínculo.  
  
 Debe actualizar common language runtime (CLR) a la versión actual que no se garantiza que funcionan con versiones anteriores. No se ejecutará el código generado con estos cambios en la versión CLR 1.x.  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)