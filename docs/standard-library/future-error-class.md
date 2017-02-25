---
title: "future_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::future_error"
dev_langs: 
  - "C++"
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# future_error (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto de excepción que se puede producir por métodos de tipos que administran objetos de [futuro](../standard-library/future-class.md) .  
  
## Sintaxis  
  
```  
class future_error : public logic_error {  
public:  
   future_error(error_code code);  
   const error_code& code() const throw();  
   const char *what() const throw();  
};  
```  
  
## Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [logic\_error \(Clase\)](../standard-library/logic-error-class.md)   
 [error\_code \(Clase\)](../standard-library/error-code-class.md)