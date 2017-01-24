---
title: "Usar operadores de extracci&#243;n | Microsoft Docs"
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
  - ">> (operador), operadores de extracción"
  - "operadores de extracción"
  - "operadores [C++], extracción"
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar operadores de extracci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de extracción \(`>>`\), que se preprograma para todos los tipos de datos estándar de C\+\+, es la manera más fácil de obtener bytes de un objeto del flujo de entrada.  
  
 Los operadores de extracción de entrada de texto con formato dependen de espacio en blanco para separar valores de datos entrantes.  Esto es difícil cuando un campo de texto contiene varias palabras o cuando las comas separan los números.  En este caso, una alternativa consiste en utilizar la función sin formato [istream::getline](../Topic/basic_istream::getline.md) miembro de entrada para leer un bloque de texto con el espacio en blanco incluido, se analiza el bloque con funciones especiales.  Otro método consiste en derivar una clase del flujo de entrada con una función miembro como `GetNextToken`, que pueden llamar a los miembros de istream para extraer y los datos de carácter de formato.  
  
## Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)