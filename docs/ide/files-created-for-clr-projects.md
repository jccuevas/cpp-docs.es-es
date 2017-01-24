---
title: "Archivos creados para proyectos de CLR | Microsoft Docs"
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
  - "aplicaciones .NET, C++"
  - "proyectos de Visual C++, programación en CLR"
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos creados para proyectos de CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al utilizar plantillas de Visual C\+\+ para crear proyectos, se crean varios archivos en función de la plantilla utilizada.  En la tabla siguiente se enumeran todos los archivos creados por plantillas de proyecto para los proyectos .NET Framework.  
  
|Nombre de archivo|Descripción del archivo|  
|-----------------------|-----------------------------|  
|AssemblyInfo.cpp|Archivo que contiene información \(es decir, atributos, archivos, recursos, tipos, información de versión, información de firma, etc.\) para modificar los metadatos de ensamblado del proyecto.  Para obtener más información, vea [Conceptos de ensamblado](../Topic/Assembly%20Contents.md).|  
|*nombre\_de\_proyecto*.asmx|Archivo de texto que hace referencia a clases administradas que encapsulan la funcionalidad del servicio Web XML.|  
|*nombre\_de\_proyecto*.cpp|Archivo de código fuente principal y punto de entrada a la aplicación creado automáticamente por Visual Studio.  Identifica el archivo .dll del proyecto y el espacio de nombres.  Incluya su propio código en este archivo.|  
|*nombre\_de\_proyecto*.vsdisco|Archivo XML de implementación que contiene vínculos a otros recursos que describen el servicio Web XML.|  
|*nombre\_de\_proyecto*.h|Archivo de inclusión principal para el proyecto, que contiene todas las declaraciones, símbolos globales y directivas `#include` para otros archivos de encabezado.|  
|*nombre\_de\_proyecto*.sln|Archivo de solución utilizado dentro del entorno de desarrollo para organizar todos los elementos del proyecto dentro de una única solución.|  
|*nombre\_de\_proyecto*.suo|Archivo de opciones de solución utilizado dentro del entorno de desarrollo.|  
|*projname.vcxproj*|Archivo de proyecto utilizado dentro del entorno de desarrollo que almacena la información específica para este proyecto.|  
|ReadMe.txt|Archivo que describe cada archivo del proyecto utilizando los nombres de archivo reales creados por la plantilla.|