---
title: "Estrategias de internacionalizaci&#243;n | Microsoft Docs"
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
  - "juegos de caracteres [C++], estrategias de programación internacional"
  - "globalización [C++], juegos de caracteres"
  - "código portable entre lenguajes [C++]"
  - "localización [C++], juegos de caracteres"
  - "MBCS [C++], estrategias de internacionalización"
  - "Unicode [C++], globalizar aplicaciones"
  - "Win32 [C++], estrategias de programación internacional"
  - "API de Windows [C++], estrategias de programación internacional"
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Estrategias de internacionalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En función de los mercados y sistemas operativos de destino, existen varias estrategias de internacionalización:  
  
-   La aplicación utiliza Unicode y, por lo tanto, se puede ejecutar en Windows 2000 y Windows NT, pero no en Windows 95 ni en Windows 98.  
  
     Se utiliza la funcionalidad específica de Unicode y todos los caracteres tienen un ancho de 16 bits \(aunque se pueden utilizar caracteres ANSI en algunas partes del programa para casos especiales\).  La biblioteca en tiempo de ejecución de C proporciona funciones, macros y tipos de datos para programar solamente en Unicode.  MFC está totalmente habilitado para Unicode.  
  
-   La aplicación utiliza MBCS y puede ejecutarse en cualquier plataforma Win32.  
  
     Se utiliza la funcionalidad específica de MBCS.  Las cadenas pueden contener caracteres de un solo byte, caracteres de doble byte, o ambos tipos de caracteres.  La biblioteca en tiempo de ejecución de C proporciona funciones, macros y tipos de datos para programar solamente en MBCS.  MFC está totalmente habilitado para MBCS.  
  
-   El código fuente para la aplicación está creado para que tenga una portabilidad total; mediante la recompilación con los símbolos **\_UNICODE** o **\_MBCS** definidos, se pueden producir versiones que utilicen cualquiera de los dos.  Para obtener más información, vea [Asignaciones de texto genérico en Tchar.h](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md).  
  
-   La aplicación utiliza una biblioteca de contenedor para las funciones Unicode que faltan en, se puede Ejecutar, y Windows ME como la que se describe en [Diseñar una única aplicación Unicode que se ejecuta en Both Windows 98 y Windows 2000](http://go.microsoft.com/fwlink/p/?LinkId=250770).  Las bibliotecas de contenedor también están disponibles comercialmente.  
  
     Se utilizan macros, tipos de datos y funciones en tiempo de ejecución de C totalmente portables.  La flexibilidad de MFC admite cualquiera de estas estrategias.  
  
 Los temas restantes se centran en la creación de código totalmente portable que se puede generar como Unicode o como MBCS.  
  
## Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Configuraciones regionales y páginas de códigos](../text/locales-and-code-pages.md)