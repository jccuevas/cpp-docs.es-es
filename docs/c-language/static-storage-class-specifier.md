---
title: "static (Especificador de clase de almacenamiento) | Microsoft Docs"
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
  - "especificadores de clases de almacenamiento estáticas"
  - "variables estáticas, especificador"
  - "clases de almacenamiento, static"
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# static (Especificador de clase de almacenamiento)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una variable declarada en el nivel interno con el especificador de clase de almacenamiento **static** tiene una duración global pero solo es visible dentro del bloque en el que se declara.  Para las cadenas constantes, el uso de **static** es útil porque palía la sobrecarga de inicialización frecuente en funciones invocadas con frecuencia.  
  
## Comentarios  
 Si no se inicializa explícitamente una variable **static**, se inicializa en 0 de forma predeterminada.  Dentro de una función, **static** hace que el almacenamiento se asigne y actúa como una definición.  Las variables estáticas internas proporcionan almacenamiento permanente privado que es visible solamente a una única función.  
  
## Vea también  
 [Estático](../misc/static-cpp.md)