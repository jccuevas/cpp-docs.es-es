---
title: "Redistribuir controles ActiveX de Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [C++], distribuir"
  - "controles [C++], redistribuir"
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Redistribuir controles ActiveX de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 6.0 proporciona controles ActiveX que puede utilizar en las aplicaciones que va a redistribuir.  Estos controles ya no se incluyen en Visual C\+\+.  Según los contratos de licencia de Visual C\+\+ 6.0, puede redistribuir estos controles con las aplicaciones desarrolladas en Visual C\+\+.  
  
> [!NOTE]
>  Microsoft no admite ya Visual C\+\+ 6.0.  
  
 Para ver una lista de los controles ActiveX redistribuibles de Visual C\+\+ 6.0, vea Common\\Redist\\Redist.txt en el disco 1 del CD de producto de Visual C\+\+ 6.0.  
  
 Al distribuir aplicaciones, debe instalar y registrar el archivo .ocx del control ActiveX \(con Regsvr32.exe\).  Asimismo, deberá asegurarse de que el equipo de destino tiene las versiones más actuales de los siguientes archivos del sistema \(un asterisco indica que es necesario registrar el archivo\):  
  
-   Asycfilt.dll  
  
-   Comcat.dll \*  
  
-   Oleaut32.dll \*  
  
-   Olepro32.dll \*  
  
-   Stdole2.tlb  
  
 Si estos archivos DLL no están disponibles en el equipo de destino, deberá obtener una copia actualizada con el mecanismo indicado para actualizar el sistema operativo correspondiente.  Puede descargar los últimos Service Pack de los sistemas operativos Windows de [http:\/\/windowsupdate.microsoft.com](http://windowsupdate.microsoft.com).  
  
 Si la aplicación utiliza un control ActiveX que se conecta a una base de datos, deberá instalar MDAC \(Microsoft Data Access Components\) en el equipo de destino.  Para obtener más información, vea [Redistribuir archivos de compatibilidad con bases de datos](../ide/redistributing-database-support-files.md).  
  
 Al utilizar un control ActiveX que se conecta a una base de datos, también es necesario replicar el nombre del origen de datos en el equipo de destino.  Puede hacerlo mediante programación con funciones como `ConfigDSN`.  
  
 Algunos controles ActiveX redistribuibles poseen dependencias adicionales.  Por cada archivo .ocx de la carpeta Os\\System del CD de producto de Visual C\+\+ 6.0, hay un archivo .dep.  Por cada archivo .ocx que desee redistribuir, busque una o varias entradas USES en el archivo .dep correspondiente.  Si un archivo aparece en la lista, deberá comprobar que existe en el equipo de destino.  Todas las DLL requeridas de forma directa para la compatibilidad con un archivo .ocx deben registrarse.  Para que Regsvr32.exe funcione correctamente, el equipo de destino debe contener todas las DLL que carga el control estáticamente. Igualmente, si un archivo DLL enumerado como dependencia también posee un archivo .dep en la carpeta Os\\System del CD de Visual C\+\+ 6.0, deberá buscar entradas USES en dicho archivo.  
  
## Vea también  
 [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md)