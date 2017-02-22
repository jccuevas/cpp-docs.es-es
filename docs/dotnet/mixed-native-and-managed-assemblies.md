---
title: "Ensamblados mixtos (nativos y administrados) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], ensamblados mixtos"
  - "ensamblados [C++], mixtos"
  - "interoperabilidad [C++], ensamblados mixtos"
  - "interoperabilidad [C++], ensamblados mixtos"
  - "código administrado [C++], interoperabilidad"
  - "ensamblados mixtos [C++]"
  - "ensamblados mixtos [C++], acerca de los ensamblados mixtos"
  - "carga de DLL mixtas [C++]"
  - "código nativo [C++], .interoperabilidad de NET"
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# Ensamblados mixtos (nativos y administrados)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los ensamblados mixtos son capaces de contener tanto instrucciones máquina no administradas como instrucciones MSIL.  Esto les permite llamar y ser llamados por componentes .NET, a la vez que conservan la compatibilidad con componentes totalmente no administrados.  Mediante ensamblados mixtos, los desarrolladores pueden crear aplicaciones con una combinación de funcionalidad administrada y no administrada.  Esto crea ensamblados mixtos ideales para migrar aplicaciones existentes de Visual C\+\+ a la plataforma .NET.  
  
 Por ejemplo, una aplicación existente que sólo consta de funciones no administradas se puede llevar a la plataforma .NET volviendo a compilar sólo un módulo con el modificador de compilación **\/clr**.  Este módulo puede utilizar las características de .NET pero sigue siendo compatible con el resto de la aplicación.  De esta manera, una aplicación se puede convertir a la plataforma .NET de un modo gradual, por partes.  Incluso es posible decidir entre compilación administrada y no administrada por funciones dentro del mismo archivo \(vea [managed, unmanaged](../preprocessor/managed-unmanaged.md)\).  
  
 Visual C\+\+ admite la generación de tres tipos distintos de ensamblados administrados: mixto, puro y comprobable.  Los dos últimos se explican en [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## En esta sección  
 [Cómo: Migrar a \/clr](../dotnet/how-to-migrate-to-clr.md)  
 Describe los pasos recomendados para introducir o actualizar la funcionalidad de .NET en la aplicación.  
  
 [Cómo: Compilar código de MFC y ATL mediante \/clr](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 Explica cómo compilar los programas MFC y ATL existentes para usarlos en Common Language Runtime.  
  
 [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)  
 Describe el problema del "bloqueo del cargador" y soluciones.  
  
 [Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)  
 Explica cómo utilizar bibliotecas nativas en compilaciones **\/clr**.  
  
 [Consideraciones sobre el rendimiento](../dotnet/performance-considerations-for-interop-cpp.md)  
 Describe las implicaciones de rendimiento de los ensamblados mixtos y el cálculo de referencias de datos.  
  
 [Dominios de aplicación y Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)  
 Explica la compatibilidad de Visual C\+\+ para dominios de aplicación.  
  
 [Doble thunk](../dotnet/double-thunking-cpp.md)  
 Trata de las implicaciones de rendimiento de un punto de entrada nativo para una función administrada.  
  
 [Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con \/clr](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 Explica cómo garantizar un apagado correcto de una aplicación administrada que utiliza un objeto COM compilado con **\/clr**.  
  
 [Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT](../dotnet/create-a-partially-trusted-application.md)  
 Explica cómo crear una aplicación de Common Language Runtime que no es de plena confianza mediante [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], quitando la dependencia de msvcm90.dll.  
  
 Para obtener más información sobre cómo codificar instrucciones para los ensamblados mixtos, vea el artículo de MSDN de información general sobre la interoperabilidad del código administrado y no administrado en [http:\/\/msdn.microsoft.com\/netframework\/default.aspx?pull\=\/library\/dndotnet\/html\/manunmancode.asp](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp).  
  
## Vea también  
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)