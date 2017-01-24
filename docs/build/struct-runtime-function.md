---
title: "RUNTIME_FUNCTION (Estructura) | Microsoft Docs"
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
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# RUNTIME_FUNCTION (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El control de excepciones basado en tabla requiere una entrada de tabla para todas las funciones que asignan espacio de la pila o llaman a otra función \(por ejemplo, funciones no de hoja\).  Las entradas de tabla de funciones tienen el formato:  
  
|||  
|-|-|  
|ULONG|Dirección de inicio de la función|  
|ULONG|Dirección de fin de la función|  
|ULONG|Dirección de información de desenredo|  
  
 El struct RUNTIME\_FUNCTION debe ser DWORD alineada en memoria.  Todas las direcciones son relativas a imágenes, es decir, que son desplazamientos de 32 bits a partir de la dirección inicial de la imagen que contiene la entrada de tabla de la función.  Estas entradas están ordenadas y se colocan en la sección .pdata de una imagen PE32\+.  Para funciones generadas dinámicamente \[compiladores JIT\], el tiempo de ejecución para admitir estas funciones debe usar RtlInstallFunctionTableCallback o RtlAddFunctionTable para proporcionar esta información al sistema operativo.  De no hacerse así, el control de excepciones y la depuración de procesos no serían confiables.  
  
## Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)