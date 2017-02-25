---
title: "Escribir manipuladores propios sin argumentos | Microsoft Docs"
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
  - "manipuladores"
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Escribir manipuladores propios sin argumentos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los manipuladores de escritura que no utilizan argumentos requieren ni la derivación de clase ni el uso de macros complejas.  Supongamos que la impresora requiere ESC \<\>de pares \[activar el modo negrita.  Puede insertar este par directamente en la secuencia:  
  
```  
cout << "regular " << '\033' << '[' << "boldface" << endl;  
```  
  
 O puede definir el manipulador de `bold` , que inserta caracteres:  
  
```  
ostream& bold( ostream& os ) {  
    return os << '\033' << '[';  
}  
cout << "regular " << bold << "boldface" << endl;  
```  
  
 La función global definido de `bold` toma un argumento de referencia de `ostream` y devuelve la referencia de `ostream` .  No es una función miembro o una función friend porque no necesita el acceso a los elementos private de la clase.  La función de `bold` conecta con la secuencia porque sobrecarga el operador de `<<` de secuencia para aceptar ese tipo de función, mediante una declaración al siguiente:  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     
   // call ios_base manipulator  
   (*_Pfn)(*(ios_base *)this);  
   return (*this);  
}  
```  
  
 Puede utilizar esta característica para extender otros operadores sobrecargados.  En este caso, es manera casual que `bold` inserta los caracteres de la secuencia.  La función se llama cuando se inserta en la secuencia, no necesariamente cuando se imprimen los caracteres adyacentes.  Así, la impresión se puede retrasar debido al búfer de la secuencia.  
  
## Vea también  
 [Flujos de salida](../standard-library/output-streams.md)