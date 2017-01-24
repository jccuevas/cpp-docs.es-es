---
title: "Funciones globales COM del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), compatibilidad con COM"
  - "COM, compatibilidad del compilador"
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones globales COM del compilador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Están disponibles las siguientes rutinas:  
  
|Función|Descripción|  
|-------------|-----------------|  
|[\_com\_raise\_error](../cpp/com-raise-error.md)|Produce un [\_com\_error](../cpp/com-error-class.md) en respuesta a un error.|  
|[\_set\_com\_error\_handler](../cpp/set-com-error-handler.md)|Reemplaza la función predeterminada que se utiliza para el control de errores de COM.|  
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convierte un valor `BSTR` en un **char \***.|  
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convierte un valor **char \*** en `BSTR`.|  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [Compatibilidad con COM del compilador](../cpp/compiler-com-support.md)