---
title: "C&#243;mo: Proporcionar funciones de trabajo a las clases call y transformer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "call (clase), ejemplo"
  - "usar la clase transformer [Runtime de simultaneidad]"
  - "usar la clase call [Runtime de simultaneidad]"
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Proporcionar funciones de trabajo a las clases call y transformer
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se ilustran varias maneras de proporcionar funciones de trabajo a las clases [concurrency::call](../../parallel/concrt/reference/call-class.md) y [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md).  
  
 En el primer ejemplo se muestra cómo pasar una expresión lambda a un objeto `call`.  En el segundo ejemplo se muestra cómo pasar un objeto de función a un objeto `call`.  En el tercer ejemplo se muestra cómo enlazar un método de clase a un objeto `call`.  
  
 Para que sirva de ilustración, cada ejemplo en este tema usa la clase `call`.  Para obtener un ejemplo de uso de la clase `transformer`, vea [Cómo: Usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra una manera común de usar la clase `call`:  En este ejemplo se pasa una función lambda al constructor `call`.  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **13 squared is 169.**   
## Ejemplo  
 El siguiente ejemplo se parece el anterior, sólo que usa la clase `call` junto con un objeto de función \(functor\).  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## Ejemplo  
 El siguiente ejemplo se parece el anterior, salvo en que usa las funciones [std::bind1st](../Topic/bind1st%20Function.md) y [std::mem\_fun](../Topic/mem_fun%20Function.md) para enlazar un objeto `call` a un método de clase.  
  
 Use esta técnica si tiene que enlazar un objeto `call` o `transformer` a un método de clase concreto en lugar del operador de llamada de función, `operator()`.  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 También puede asignar el resultado de la función `bind1st` a un objeto [std::function](../../standard-library/function-class.md) o usar la palabra clave `auto`, tal y como se muestra en el siguiente ejemplo.  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/CPP/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `call.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc call.cpp**  
  
## Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Cómo: Usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [Clase call](../../parallel/concrt/reference/call-class.md)   
 [Clase transformer](../../parallel/concrt/reference/transformer-class.md)