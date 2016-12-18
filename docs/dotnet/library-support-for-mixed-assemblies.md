---
title: "Compatibilidad con bibliotecas para ensamblados mixtos | Microsoft Docs"
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
  - "bibliotecas [C++], ensamblados mixtos"
  - "ensamblados mixtos [C++], compatibilidad con bibliotecas"
  - "msvcm90[d].dll"
  - "msvcmrt[d].lib"
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con bibliotecas para ensamblados mixtos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ admite el uso de la biblioteca estándar de C\+\+, la biblioteca de Common RunTime \(CRT\), ATL y MFC para aplicaciones compiladas con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md).  De este modo, las aplicaciones existentes que utilizan estas bibliotecas también pueden usar las características de .NET Framework.  
  
 Esta compatibilidad presenta la nueva DLL y las bibliotecas de importación siguientes:  
  
-   Msvcmrt\[d\].lib si se compila con \/clr.  Vínculos de ensamblados mixtos a esta biblioteca de importación.  
  
-   Msvcm90\[d\].dll y Msvcurt\[d\].lib si se compila con \/clr:pure.  La DLL es un ensamblado mixto que proporciona compatibilidad con C Run Time \(CRT\) administrada y forma parte de un ensamblado administrado instalado en la caché global de ensamblados \(GAC\).  Los ensamblados puros se vinculan a esta biblioteca de importación y terminan enlazados a Msvcm90.dll.  
  
 Esta compatibilidad proporciona algunas ventajas relacionadas:  
  
-   La biblioteca estándar de C\+\+ y CRT están disponibles tanto para código mixto como puro.  La biblioteca estándar de C\+\+ y CRT proporcionadas no son comprobables; en última instancia, las llamadas se siguen derivando a las mismas biblioteca estándar de C\+\+ y CRT que se utilizan desde el código nativo.  
  
-   Corrección del control de excepciones unificado en imágenes puras y mixtas.  
  
-   Inicialización estática de variables de C\+\+ en imágenes puras y mixtas.  
  
-   Compatibilidad con variables por AppDomain y por proceso en código administrado.  
  
-   Resuelve los problemas de bloqueo del cargador que se aplican a las DLL mixtas en Visual C\+\+ .NET y Visual C\+\+ .NET 2003.  
  
 Además, esta compatibilidad tiene las siguientes limitaciones:  
  
-   Sólo el modelo de DLL de CRT es compatible \(tanto para código compilado con \/clr como con \/clr:pure\).  
  
-   Si los objetos utilizan las bibliotecas de Visual C\+\+ \(ya que todos los objetos de una imagen pura deben ser puros\), no se pueden combinar objetos puros y mixtos en una misma imagen.  Si lo hace, recibirá errores en tiempo de vínculo.  
  
 Es conveniente actualizar Common Language Runtime \(CLR\) a la versión actual, ya que no se garantiza que funcione con versiones anteriores.  El código compilado con estos cambios no se podrá ejecutar en la versión 1.x de CLR.  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)