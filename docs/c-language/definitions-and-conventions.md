---
title: "Definiciones y convenciones | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "definición de no terminales"
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Definiciones y convenciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los elementos terminales son extremos en una definición de sintaxis.  No hay ninguna otra posible resolución.  Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.  
  
 Los marcadores de posición de la sintaxis son no terminales y se definen en otras partes de este resumen de la sintaxis.  Las definiciones pueden ser recursivas.  
  
 Un componente opcional se indica mediante el subíndice opt.  Por ejemplo,  
  
```  
  
{ expression <SUB>opt</SUB> }  
```  
  
 indica una expresión opcional encerrada entre llaves.  
  
 Las convenciones de sintaxis utilizan diferentes atributos de fuente para los distintos componentes de la sintaxis.  Los símbolos y fuentes son los siguientes:  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|*elemento no terminal*|La cursiva indica elementos no terminales.|  
|**const**|Los elementos terminales en negrita son símbolos y palabras literales reservadas que deben especificarse tal como aparecen.  Los caracteres en este contexto siempre distinguen entre mayúsculas y minúsculas.|  
|opc|Los elementos no terminales seguidos de opc son siempre opcionales.|  
|tipo de letra predeterminado|Los caracteres del conjunto descrito o enumerado con este tipo de fuente se pueden usar como terminales en las instrucciones de C.|  
  
 Un signo de dos puntos \(**:**\) a continuación de un no terminal presenta su definición.  Las definiciones alternativas se enumeran en líneas independientes, excepto si van precedidas de las palabras "uno de".  
  
## Vea también  
 [Resumen de sintaxis del lenguaje C](../c-language/c-language-syntax-summary.md)