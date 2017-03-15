---
title: "/Fi (Preprocesar el nombre del archivo de salida) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Fi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fi (opción del compilador) (C++)"
  - "Fi (opción del compilador) (C++)"
  - "-Fi (opción del compilador) (C++)"
  - "preprocesar archivos de salida, nombre de archivo"
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /Fi (Preprocesar el nombre del archivo de salida)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el nombre del archivo de salida en el que la opción del compilador [\/P \(Preprocesar y escribir en un archivo\)](../../build/reference/p-preprocess-to-a-file.md) escribe la salida preprocesada.  
  
## Sintaxis  
  
```  
/Fipathname  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`pathname`|El nombre y ruta de acceso del archivo de salida generados por la opción del compilador **\/P**.|  
  
## Comentarios  
 Utilice la opción del compilador **\/Fi** en combinación con la opción del compilador **\/P**.  
  
 Si especifica solo una ruta de acceso para el parámetro `pathname`, el nombre base del archivo de origen se utiliza como el nombre base del archivo de salida preprocesado.  El parámetro `pathname` no requiere una extensión de nombre de archivo determinada.  Sin embargo, se utiliza una extensión de ".i" si no especifica una extensión de nombre de archivo.  
  
## Ejemplo  
 La línea de comandos siguiente preprocesa PROGRAM.cpp, conserva los comentarios, agrega las directivas [\#line](../../preprocessor/hash-line-directive-c-cpp.md) y escribe el resultado en el archivo MYPROCESS.i.  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [\/P \(Preprocesar y escribir en un archivo\)](../../build/reference/p-preprocess-to-a-file.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)