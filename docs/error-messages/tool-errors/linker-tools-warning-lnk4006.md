---
title: "Advertencia de las herramientas del vinculador LNK4006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4006"
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia de las herramientas del vinculador LNK4006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

symbol ya se definió en objeto; segunda definición omitida  
  
 El `symbol` dado, mostrado en su forma decorada, se definió varias veces.  Cuando se produce esta advertencia, `symbol` se agrega dos veces, pero sólo se utiliza su primera forma.  
  
 Se obtiene esta advertencia al intentar combinar dos bibliotecas importadas.  
  
 Si se recompila la biblioteca en tiempo de ejecución de C, se puede omitir el mensaje.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  El parámetro `symbol` indicado puede ser una función empaquetada, creada al compilar con [\/Gy](../../build/reference/gy-enable-function-level-linking.md).  Este símbolo se incluyó en más de un archivo pero se modificó de una compilación a otra.  Vuelva a compilar todos los archivos que incluyan el parámetro `symbol`.  
  
2.  El parámetro `symbol` indicado puede haberse definido de manera diferente en dos objetos miembro de diferentes bibliotecas.  
  
3.  Puede haberse definido un absoluto dos veces, con un valor diferente en cada definición.  
  
4.  Si se recibe este mensaje de error al combinar bibliotecas, significa que `symbol` ya existe en la biblioteca a la que se está agregando.