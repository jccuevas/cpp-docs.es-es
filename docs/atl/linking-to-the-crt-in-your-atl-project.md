---
title: "Linking to the CRT in Your ATL Project | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DllMainCRTStartup"
  - "wWinMainCRTStartup"
  - "WinMainCRTStartup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, C Run-Time library (CRT)"
  - "CRT, linking with ATL"
  - "DllMainCRTStartup method"
  - "WinMainCRTStartup method"
  - "wWinMainCRTStartup method"
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Linking to the CRT in Your ATL Project
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[Bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md) \(CRT\) proporciona muchas funciones útiles que pueden crear una programación de mucho más fácil durante el desarrollo de ATL.  Todos los vínculos de los proyectos ATL a la biblioteca CRT.  Puede ver las ventajas y desventajas de vincular método en [Ventajas y Tradeoffs del método utilizado para vincular a CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## Efectos de vincular a CRT en el programa Image The  
 Si vincula estáticamente a CRT, el código de CRT se coloca en la imagen ejecutable y no necesita tener el archivo DLL de CRT presente en un sistema para trabajar con la imagen.  Si vincula dinámicamente a CRT, las referencias al código del archivo DLL de CRT se colocan en la imagen, pero no el propio código.  Para que la imagen en un sistema determinado, el archivo DLL de CRT debe estar presente en ese sistema.  Incluso cuando se vincula dinámicamente a CRT, es posible que el código puede vincular estáticamente \(por ejemplo, **DllMainCRTStartup**\).  
  
 Cuando se enlaza la imagen, especifique explícita o implícitamente un punto de entrada que el sistema operativo llama a después de cargar la imagen.  Para el archivo DLL, el punto de entrada predeterminado es **DllMainCRTStartup**.  Para un archivo EXE, es **WinMainCRTStartup**.  Puede invalidar el valor predeterminado con la opción de vinculador \/ENTRY.  CRT proporciona una implementación para **DllMainCRTStartup**, **WinMainCRTStartup**, y **wWinMainCRTStartup** \(el punto de entrada de Unicode para EXE\).  Estos CRT\-proporcionaron constructores de llamada de los puntos de entrada en objetos globales e inicializan otras estructuras de datos que se usan en algunas funciones CRT.  Este código de inicio agrega sobre 25K a la imagen si se vincula estáticamente.  Si se vincula dinámicamente, la mayor parte del código está en un archivo DLL, por lo que el tamaño de imagen permanece pequeño.  
  
 Para obtener más información, vea el tema [\/ENTRY \(Símbolo de punto de entrada\)](../build/reference/entry-entry-point-symbol.md)del vinculador.  
  
## Opciones de optimización  
 Mediante la opción de vinculador \/OPT: NOWIN98 puede reducir más un control predeterminado ATL por 10K, a expensas de tiempo de carga de los sistemas de Windows 98.  Para obtener más información sobre vincular opciones, vea [\/OPT \(Optimizaciones\)](../build/reference/opt-optimizations.md).  
  
## Vea también  
 [Programar con ATL y código en tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Comportamiento de la biblioteca en tiempo de ejecución](../build/run-time-library-behavior.md)