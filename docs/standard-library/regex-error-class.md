---
title: "regex_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::regex_error"
  - "regex_error"
  - "std.tr1.regex_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_error (clase) [TR1]"
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Informa de un objeto basic\_regex incorrecto.  
  
## Sintaxis  
  
```  
class regex_error  
    : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);  
    regex_constants::error_code code() const;  
    };  
```  
  
## Comentarios  
 La clase describe un objeto de excepción que se produce para notificar un error en la construcción o el uso de un objeto `basic_regex`.  
  
## Requisitos  
 **Encabezado:** \<regex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_error](../standard-library/regex-error-class.md)