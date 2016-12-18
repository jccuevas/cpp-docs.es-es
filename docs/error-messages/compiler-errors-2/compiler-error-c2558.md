---
title: "Error del compilador C2558 | Microsoft Docs"
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
  - "C2558"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2558"
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2558
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': no hay un constructor de copias disponible o éste se declaró como 'explicit'  
  
 Un constructor de copias inicializa un objeto a partir de otro objeto del mismo tipo.  \(Hace una copia del objeto\). El compilador genera un constructor de copias predeterminado si no se define ningún constructor.  
  
### Para corregir este error  
  
1.  El problema puede producirse cuando se intenta copiar una clase cuyo constructor de copias es `private`.  En la mayoría de los casos, no debe copiarse una clase que tenga un constructor de copias `private`.  Una técnica de programación común consiste en declarar un constructor de copias `private` para impedir el uso directo de una clase.  La clase puede quedar inservible o requerir otra clase para poder funcionar correctamente.  
  
     Si determina que es seguro utilizar una clase que tenga un constructor de copias `private`, derive una nueva clase a partir de la clase que tiene el constructor `private` y proporcione un constructor de copias `public` o `protected` en la clase nueva.  Utilice la clase derivada en lugar de la original.  
  
2.  El problema puede producirse cuando se trata de copiar una clase cuyo constructor de copias es explícito.  Declarar un constructor de copias como `explicit` impide que se pasen objetos de una clase a las funciones o que se devuelvan objetos de una clase desde las funciones.  Para más información sobre los constructores explícitos, consulte [Conversiones](../../cpp/user-defined-type-conversions-cpp.md).  
  
3.  El problema puede producirse cuando intenta copiar una instancia de la clase declarada como `const` utilizando un constructor de copias que no toma un parámetro de referencia `const`.  Declare el constructor de copias con una referencia de tipo `const` en lugar de con una referencia de otro tipo.