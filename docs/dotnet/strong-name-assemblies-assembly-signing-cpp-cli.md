---
title: "Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI) | Microsoft Docs"
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
  - ".NET Framework [C++], firma de ensamblados"
  - "ensamblados [C++]"
  - "ensamblados [C++], firmar"
  - "vinculador [C++], firma de ensamblados"
  - "firmar ensamblados"
  - "ensamblados con nombre seguro [C++]"
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo puede firmar el ensamblado, lo que a menudo se conoce como dar un nombre seguro al ensamblado.  
  
## Comentarios  
 Cuando utilice Visual C\+\+, use las opciones del vinculador para firmar el ensamblado con el fin de evitar problemas relacionados con los atributos CLR para la firma de ensamblados:  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Entre las razones para no utilizar los atributos está el hecho de que el nombre clave es visible en los metadatos del ensamblado, lo cual puede significar un riesgo para la seguridad si el nombre de archivo incluye información confidencial.  A su vez, el proceso de compilación usado por el entorno de desarrollo de Visual C\+\+ invalidará la clave con la que está firmado el ensamblado si utiliza atributos CLR para asignar al ensamblado un nombre seguro y, a continuación, ejecuta una herramienta de procesamiento posterior como mt.exe en el ensamblado.  
  
 Si compila desde la línea de comandos, usa opciones del vinculador para firmar el ensamblado y, a continuación, ejecuta una herramienta de procesamiento posterior \(como mt.exe\), deberá volver a firmar el ensamblado con sn.exe.  De forma alternativa, puede compilar el ensamblado y retrasar su firma y, después de ejecutar herramientas de procesamiento posterior, completar la firma.  
  
 Si utiliza los atributos de firma durante la compilación en el entorno de desarrollo, puede firmar satisfactoriamente el ensamblado llamando explícitamente a sn.exe \([Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)\) en un evento posterior a la compilación.  Para obtener más información, vea [Especificar eventos de compilación](../ide/specifying-build-events.md).  Los tiempos de generación pueden ser inferiores si utiliza atributos y un evento posterior a la compilación, en lugar de utilizar las opciones de un vinculador.  
  
 Las siguientes opciones del vinculador admiten la firma de ensamblados:  
  
-   [\/DELAYSIGN \(Firmar parcialmente un ensamblado\)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE \(Especificar una clave o par de claves para firmar un ensamblado\)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER \(Especificar un contenedor de claves para firmar un ensamblado\)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Para obtener más información sobre los ensamblados con nombre seguro, vea [Crear y utilizar ensamblados con nombre seguro](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)