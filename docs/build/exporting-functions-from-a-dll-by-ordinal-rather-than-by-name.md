---
title: "Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NONAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exportar DLL [C++], valores ordinales"
  - "exportar funciones [C++], valores ordinales"
  - "NONAME (atributo)"
  - "exportaciones de ordinales [C++]"
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Exportar funciones desde un archivo DLL por ordinal en lugar de por nombre
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La forma más sencilla de exportar funciones desde el archivo DLL es exportarlas por nombre.  Esto sucede cuando utiliza **\_\_declspec\(dllexport\)**, por ejemplo.  Pero también puede exportar funciones por ordinal.  Con esta técnica, debe utilizar un archivo .def en lugar de **\_\_declspec\(dllexport\)**.  Para especificar un valor ordinal de la función, anexe su ordinal al nombre de función del archivo .def.  Para obtener más información sobre cómo especificar ordinales, vea [Exportar desde un archivo DLL mediante archivos def](../build/exporting-from-a-dll-using-def-files.md).  
  
> [!TIP]
>  Si desea optimizar el tamaño del archivo DLL, utilice el atributo **NONAME** en todas las funciones exportadas.  Con el atributo **NONAME**, los ordinales se almacenan en la tabla de exportación del archivo DLL en lugar de en los nombres de función.  Esto puede proporcionar un ahorro considerable cuando exporte muchas funciones.  
  
## ¿Qué desea hacer?  
  
-   [Utilizar un archivo .def para exportar por ordinal](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Utilizar \_\_declspec\(dllexport\)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## Vea también  
 [Exportar desde un archivo DLL](../build/exporting-from-a-dll.md)