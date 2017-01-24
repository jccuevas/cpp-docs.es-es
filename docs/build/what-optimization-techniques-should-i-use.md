---
title: "&#191;Qu&#233; t&#233;cnicas de optimizaci&#243;n se deben utilizar para mejorar el rendimiento de las aplicaciones cliente al cargarlas? | Microsoft Docs"
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
  - "DLL [C++], optimizar"
  - "optimización [C++], DLL"
  - "rendimiento [C++], DLL"
ms.assetid: 2f8bbfb5-08b9-4a35-8302-25a1966881b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &#191;Qu&#233; t&#233;cnicas de optimizaci&#243;n se deben utilizar para mejorar el rendimiento de las aplicaciones cliente al cargarlas?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el archivo DLL es un archivo DLL estándar vinculado estáticamente a MFC, al cambiarlo por un archivo DLL estándar vinculado dinámicamente a MFC se reduce el tamaño del archivo.  
  
 Si el archivo DLL tiene muchas funciones exportadas, utilice un archivo .def para exportar las funciones \(en lugar de utilizar **\_\_declspec\(dllexport\)**\) y el [atributo NONAME](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) del archivo .def en cada una de las funciones exportadas.  El atributo NONAME sólo hace que se almacene en la tabla de exportación del archivo DLL el valor ordinal \(no el nombre de la función\); esto reduce el tamaño del archivo.  
  
 Los archivos DLL que se vinculan implícitamente a una aplicación se cargarán cuando se cargue la aplicación.  Para mejorar el rendimiento de carga, intente dividir el archivo DLL en varios archivos DLL.  Coloque todas las funciones que necesite la aplicación que hace llamada inmediatamente después de la carga en un archivo DLL y vincule implícitamente la aplicación a ese archivo DLL.  Coloque en otro archivo DLL las demás funciones que la aplicación que hace la llamada no necesite inmediatamente y vincule explícitamente la aplicación a ese archivo DLL.  Para obtener más información, vea [Determinar el método de vinculación que se debe utilizar](../build/determining-which-linking-method-to-use.md).  
  
## Vea también  
 [Preguntas más frecuentes sobre archivos DLL](../build/dll-frequently-asked-questions.md)