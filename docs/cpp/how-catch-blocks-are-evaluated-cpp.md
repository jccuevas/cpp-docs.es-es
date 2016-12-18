---
title: "C&#243;mo se eval&#250;an los bloques catch (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, catch (controladores)"
  - "catch (palabra clave) [C++], tipos de controladores catch"
  - "control de excepciones, detectar y eliminar excepciones"
  - "try-catch (palabra clave) [C++], tipos que pueden detectarse"
  - "tipos [C++], control de excepciones"
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo se eval&#250;an los bloques catch (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ permite iniciar excepciones de cualquier tipo, aunque en general se recomienda iniciar tipos derivados de std::exception.  Una excepción de C\+\+ se puede detectar mediante un controlador **catch** que especifique el mismo tipo que la excepción, o mediante un controlador que pueda detectar cualquier tipo de excepción.  
  
 Si el tipo de excepción que se inicia es una clase, que también tiene una o varias clases base, se puede detectar mediante los controladores que aceptan las clases base del tipo de la excepción, así como referencias a las bases del tipo de la excepción.  Observe que, cuando una referencia detecta una excepción, está enlazada al objeto de excepción real que se ha iniciado; si no, es una copia \(igual que un argumento de una función\).  
  
 Cuando se inicia una excepción, se puede detectar mediante los siguientes tipos de controladores **catch**:  
  
-   Un controlador que pueda aceptar cualquier tipo \(mediante la sintaxis de puntos suspensivos\).  
  
-   Un controlador que acepte el mismo tipo que el objeto de excepción; dado que es una copia, se omiten los modificadores **const** y `volatile`.  
  
-   Un controlador que acepte una referencia al mismo tipo que el objeto de excepción.  
  
-   Un controlador que acepte una referencia a una forma **const** o `volatile` del mismo tipo que el objeto de excepción.  
  
-   Un controlador que acepte una clase base del mismo tipo que el objeto de excepción; dado que es una copia, se omiten los modificadores **const** y `volatile`.  El controlador **catch** para una clase base no debe preceder al controlador **catch** para la clase derivada.  
  
-   Un controlador que acepte una referencia a una clase base del mismo tipo que el objeto de excepción.  
  
-   Un controlador que acepte una referencia a una forma **const** o `volatile` de una clase base del mismo tipo que el objeto de excepción.  
  
-   Un controlador que acepte un puntero al que pueda convertirse un objeto de puntero iniciado mediante las reglas de conversión de puntero estándar.  
  
 El orden en que los controladores **catch** aparecen es importante, porque los controladores para un bloque **try** determinado se examinan por orden de aparición.  Por ejemplo, es un error colocar el controlador para una clase base antes del controlador para una clase derivada.  Una vez encontrado un controlador **catch** coincidente, no se examinan los controladores subsiguientes.  Como resultado, un controlador **catch** de puntos suspensivos debe ser el último controlador de su bloque **try**.  Por ejemplo:  
  
```  
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 En este ejemplo, el controlador **catch** de puntos suspensivos es el único controlador que se examina.  
  
## Vea también  
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)