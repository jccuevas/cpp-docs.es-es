---
title: "Error del compilador C2026 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2026"
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cadena demasiado grande; caracteres finales truncados  
  
 La cadena sobrepasaba el límite de 16380 caracteres de un solo byte.  
  
 Antes de la concatenación de cadenas adyacentes, una cadena no puede sobrepasar los 16380 caracteres de un solo byte.  
  
 Una cadena Unicode de alrededor de la mitad de esta longitud generaría también este error.  
  
 Si una cadena está definida como sigue, se generará un error C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 Puede dividirla de la siguiente forma:  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 Es aconsejable almacenar en un recurso personalizado o en un archivo externo los literales de cadenas excepcionalmente largas \(32 K o más\).  Vea [Crear un nuevo recurso personalizado o recurso de datos](../../mfc/creating-a-new-custom-or-data-resource.md) para obtener más información.