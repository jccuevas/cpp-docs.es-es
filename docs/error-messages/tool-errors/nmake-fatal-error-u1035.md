---
title: "Error grave de NMAKE U1035 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1035"
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : se esperaba el separador ':' o '\='  
  
 Se esperaba un signo de dos puntos \(**:**\) o un signo igual \(**\=**\).  
  
### Posibles causas del error:  
  
1.  Un destino no iba seguido de un signo de dos puntos.  
  
2.  A continuación de un destino de una sola letra se ha incluido un signo de dos puntos sin espacio intermedio \(por ejemplo, un:\).  NMAKE lo ha interpretado como una especificación de unidad.  
  
3.  Una regla de inferencia no iba seguida de un signo de dos puntos.  
  
4.  Una definición de macro no iba seguida de un signo igual.  
  
5.  Se ha utilizado un carácter seguido de una barra inversa \(**\\**\) para continuar un comando en una nueva línea.  
  
6.  Se ha utilizado una cadena que no sigue ninguna regla de sintaxis NMAKE.  
  
7.  El archivo MAKE ha recibido formato de un procesador de textos.