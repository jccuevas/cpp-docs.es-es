---
title: "Acceso a datos mediante ADO.NET (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - ".NET Framework [C++], acceso a datos"
  - "ADO.NET [C++]"
  - "datos [C++], ADO.NET"
  - "acceso a datos [C++], ADO.NET"
  - "bases de datos [C++], tener acceso en C++"
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Acceso a datos mediante ADO.NET (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ADO.NET es la API de .NET Framework para el acceso a datos y proporciona una capacidad y facilidad de uso inigualables comparadas con las soluciones de acceso a datos anteriores.  En esta sección se describen algunos de los problemas que afectan a ADO.NET que son exclusivos de los usuarios de Visual C\+\+, como el cálculo de referencias de tipos nativos.  
  
 ADO.NET se ejecuta bajo el Common Language Runtime \(CLR\).  Por consiguiente, cualquier aplicación que interactúe con ADO.NET también deberá estar destinada al CLR.  No obstante, eso no significa que las aplicaciones nativas no puedan usar ADO.NET.  Estos ejemplos explicarán cómo interactuar con una base de datos ADO.NET desde código nativo.  
  
## En esta sección  
 [Cómo: Calcular las referencias de cadenas ANSI para ADO.NET](../dotnet/how-to-marshal-ansi-strings-for-adonet-cpp-cli.md)  
  
 [Cómo: Calcular las referencias de cadenas BSTR para ADO.NET](../dotnet/how-to-marshal-bstr-strings-for-adonet-cpp-cli.md)  
  
 [Cómo: Calcular las referencias de cadenas Unicode para ADO.NET](../dotnet/how-to-marshal-unicode-strings-for-adonet-cpp-cli.md)  
  
 [Cómo: Calcular las referencias de un tipo de datos VARIANT para ADO.NET](../dotnet/how-to-marshal-a-variant-for-adonet-cpp-cli.md)  
  
 [Cómo: Calcular las referencias de una matriz SAFEARRAY para ADO.NET](../dotnet/how-to-marshal-a-safearray-for-adonet-cpp-cli.md)  
  
## Secciones relacionadas  
  
|Sección|Descripción|  
|-------------|-----------------|  
|[ADO.NET](../Topic/ADO.NET.md)|Proporciona información general sobre ADO.NET, un conjunto de clases que exponen los servicios de acceso a datos al programador de .NET.|  
|[Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/es-es/5358a825-e19b-49aa-8214-674ce5fed1da)|Describe cómo utilizar los lenguajes de .NET, incluido Visual C\+\+, para crear objetos de base de datos como procedimientos almacenados, agregados, desencadenadores, funciones definidas por el usuario y tipos definidos por el usuario; así como la forma de recuperar y actualizar datos para bases de datos de Microsoft SQL Server 2005.|  
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)