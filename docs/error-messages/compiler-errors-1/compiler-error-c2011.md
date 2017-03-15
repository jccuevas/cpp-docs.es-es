---
title: "Error del compilador C2011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2011"
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': nueva definición del tipo 'type'  
  
 El identificador ya se ha definido como `type`.  Busque nuevas definiciones del identificador.  
  
 También puede generarse el error C2011 si se importa varias veces un archivo de encabezado o una biblioteca de tipos al mismo archivo.  Para evitar inclusiones múltiples de los tipos definidos en un archivo de encabezado, aplique a este archivo restricciones de inclusión o una directiva [once](../../preprocessor/once.md) de `#pragma`.  
  
 Si necesita encontrar la declaración inicial del tipo redefinido, use la marca de compilador [\/P](../../build/reference/p-preprocess-to-a-file.md) para generar el resultado preprocesado que se ha pasado al compilador.  Con las herramientas de búsqueda de texto, puede buscar instancias del identificador redefinido en el archivo de salida.  
  
 El ejemplo siguiente genera el error C2011 y muestra cómo corregirlo:  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```