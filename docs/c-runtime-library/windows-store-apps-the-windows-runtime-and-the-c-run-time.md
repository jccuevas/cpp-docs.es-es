---
title: Aplicaciones de la Tienda Windows, Windows Runtime y runtime de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c75d66fcbe9ef437980878e7789a82dc94b68573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windows-store-apps-the-windows-runtime-and-the-c-run-time"></a>Aplicaciones de la Tienda Windows, Windows Runtime y runtime de C
Las aplicaciones de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] son programas que se ejecutan en Windows Runtime que se ejecuta en [!INCLUDE[win8](../build/reference/includes/win8_md.md)].  Windows Runtime es un entorno de confianza que controla las funciones, las variables y los recursos que están disponibles para una aplicación [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]. Sin embargo, por diseño, las restricciones de Windows Runtime impiden el uso de la mayoría de las características de la biblioteca en tiempo de ejecución de C (CRT) en las aplicaciones de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)].  
  
 Windows Runtime no admite las siguientes características de CRT:  
  
-   La mayoría de las funciones de CRT que están relacionadas con cierta funcionalidad no admitida.  
  
     Por ejemplo, una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] no puede crear un proceso mediante las familias de rutinas de `exec` y `spawn`.  
  
     Cuando una función de CRT no se admite en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)], este hecho se indica expresamente en su artículo de referencia.  
  
-   La mayoría de las funciones de cadena y carácter multibyte.  
  
     Sin embargo, se admiten texto Unicode y ANSI.  
  
-   Los argumentos de aplicaciones de consola y de la línea de comandos.  
  
     Sin embargo, las aplicaciones de escritorio tradicionales siguen admitiendo los argumentos de consola y de la línea de comandos.  
  
-   Variables de entorno.  
  
-   El concepto de un directorio de trabajo actual.  
  
-   Las aplicaciones y los archivos DLL de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] que están vinculados estáticamente a CRT y que se compilan con las opciones del compilador [/MT](../build/reference/md-mt-ld-use-run-time-library.md) o `/MTd`.  
  
     Es decir, una aplicación que usa una versión estática multiproceso de CRT.  
  
-   Una aplicación que se compila mediante la opción del compilador [/MDd](../build/reference/md-mt-ld-use-run-time-library.md).  
  
     Es decir, una versión de depuración multiproceso y específica para DLL de CRT. Dicha aplicación no se admite en [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)].  
  
 Para obtener una lista completa de las funciones de CRT que no están disponibles en una aplicación de [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] y sugerencias sobre funciones alternativas, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)   
 [Funciones de CRT no compatibles con Windows Runtime](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)   
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)