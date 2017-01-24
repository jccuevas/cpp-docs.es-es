---
title: "Decoraci&#243;n de nombres | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nombres representativos, convenciones de llamada"
  - "decoración de nombres [C++]"
  - "nombres [C++], representativos"
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Decoraci&#243;n de nombres
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La decoración de nombres normalmente hace referencia a las convenciones de nomenclatura de C\+\+, pero también se puede aplicar a varios casos de C.  De forma predeterminada, C\+\+ usa el nombre de la función, los parámetros y el tipo de valor devuelto para crear un nombre del vinculador para la función.  Considere la siguiente función:  
  
```  
void CALLTYPE test(void)  
```  
  
 En la tabla siguiente se muestra el nombre del vinculador para varias convenciones de llamada.  
  
|Convención de llamada|archivo de extern "C" o .c|.cpp, .cxx o \/TP|  
|---------------------------|--------------------------------|-----------------------|  
|Convención de nomenclatura de C \(`__cdecl`\)|\_test|?test@@ZAXXZ|  
|Convención de nomenclatura de fastcall \(`__fastcall`\)|@test@0|?test@@YIXXZ|  
|Convención de nomenclatura de llamada estándar \(`__stdcall`\)|\_test@0|?test@@YGXXZ|  
|Convención de nomenclatura de Vectorcall \(`__vectorcall`\)|test@@0|?test@@YQXXZ|  
  
 Use extern "C" para llamar a una función de C desde C\+\+.  Extern "C" fuerza el uso de la convención de nomenclatura de C para funciones C\+\+ no de clases.  Tenga en cuenta los modificadores de compilador **\/Tc** y **\/Tp**, que indican al compilador que omita la extensión de nombre de archivo y compile el archivo como C o C\+\+, respectivamente.  Estas opciones pueden dar lugar a nombres inesperados.  
  
 Tener prototipos de función con parámetros no coincidentes también puede producir este error.  La decoración de nombres incorpora los parámetros de una función en el nombre de función representativo final.  Llamar a una función con tipos de parámetro que no coinciden con los de la declaración de función también puede generar el error LNK2001.  
  
 Actualmente, no hay un estándar de denominación entre fabricantes de compiladores, ni entre versiones diferentes de un compilador de C\+\+.  Por ello, vincular archivos objeto compilados con otros compiladores puede no producir el mismo esquema de denominación y causar externos sin resolver.  
  
## Vea también  
 [Error de las herramientas del vinculador LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)