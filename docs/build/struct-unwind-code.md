---
title: "UNWIND_CODE (Estructura) | Microsoft Docs"
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
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# UNWIND_CODE (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La matriz de códigos de desenredo se utiliza para registrar la secuencia de operaciones en el prólogo que afectan a los registros no variables y RSP.  Cada elemento de código tiene el formato siguiente:  
  
|||  
|-|-|  
|UBYTE|Desplazamiento en el prólogo|  
|UBYTE: 4|Código de operación de desenredo|  
|UBYTE: 4|Información de la operación|  
  
 La matriz se organiza por orden descendente de desplazamiento en el prólogo.  
  
 **Desplazamiento en el prólogo**  
 El desplazamiento desde el principio del prólogo del final de la instrucción que efectúa esta operación, más 1 \(es decir, el desplazamiento del inicio de la siguiente instrucción\).  
  
 **Código de operación de desenredo**  
 Nota: Ciertos códigos de operación requieren un desplazamiento sin signo a un valor en el marco de pila local.  Este desplazamiento es desde el inicio \(dirección más baja\) de la asignación de espacio fijo de la pila.  Si el campo Frame Register de UNWIND\_INFO es cero, este desplazamiento se realiza desde RSP.  En caso contrario, se trata del desplazamiento desde la ubicación de RSP cuando se estableció el registro de FP.  Esto es igual al registro de FP menos el desplazamiento del registro de FP \(16 \* el desplazamiento del registro del marco con cambio de escala en UNWIND\_INFO\).  Si se utiliza un registro de FP, todo código de desenredo que tome un desplazamiento sólo deberá utilizarse después de haber establecido el registro de FP en el prólogo.  
  
 Para todos los códigos de operación excepto UWOP\_SAVE\_XMM128 y UWOP\_SAVE\_XMM128\_FAR, el desplazamiento siempre será un múltiplo de 8, porque todos los valores de interés de la pila se almacenan en límites de 8 bytes \(la propia pila siempre tiene alineación de 16 bytes\).  Para códigos de operación con un desplazamiento corto \(menos de 512 K\), el valor USHORT final en los nodos para este código mantiene el desplazamiento dividido por 8.  Para códigos de operación con un desplazamiento largo \(512 K \<\= desplazamiento \< 4 GB\), los dos nodos de USHORT finales para este código mantienen el desplazamiento \(en formato little\-endian\).  
  
 Para los códigos de operación UWOP\_SAVE\_XMM128 y UWOP\_SAVE\_XMM128\_FAR, el desplazamiento siempre será múltiplo de 16, ya que todas las operaciones XMM de 128 bits se deben producir en memoria con alineación de 16 bytes.  Por consiguiente, se utiliza un factor de la escala de 16 para UWOP\_SAVE\_XMM128, permitiendo desplazamientos de menos de 1 M.  
  
 El código de operación de desenredo es uno de los siguientes:  
  
 UWOP\_PUSH\_NONVOL \(0\)1 nodo  
  
 Insertan un registro entero no variable, disminuyendo RSP en 8.  La información de la operación es el número del registro.  Tenga en cuenta que, debido a las restricciones en los epílogos, los códigos de desenredo de UWOP\_PUSH\_NONVOL deben aparecer primero en el prólogo y, correspondientemente, los últimos en la matriz de códigos de desenredo.  Esta ordenación relativa se aplica a todos los otros códigos de desenredo excepto UWOP\_PUSH\_MACHFRAME.  
  
 UWOP\_ALLOC\_LARGE \(1\)2 o 3 nodos  
  
 Asignan un área de grandes dimensiones en la pila.  Hay dos formas.  Si la información de la operación es igual a 0, el tamaño de la asignación dividido por 8 se registra en la siguiente ranura, permitiendo una asignación de hasta 512 K \- 8.  Si la información de la operación es igual a 1, el tamaño de la asignación sin cambio de escala se registra en las dos siguientes ranuras en formato little\-endian, permitiendo asignaciones de hasta 4 GB \- 8.  
  
 UWOP\_ALLOC\_SMALL \(2\)1 nodo  
  
 Asignan un área de pequeñas dimensiones en la pila.  El tamaño de la asignación es el campo de información de la operación \* 8 \+ 8, permitiendo asignaciones de 8 a 128 bytes.  
  
 El código de desenredo para una asignación de la pila siempre debería utilizar la codificación más corta posible:  
  
|||  
|-|-|  
|**Tamaño de asignación**|**Código de desenredo**|  
|8 a 128 bytes|UWOP\_ALLOC\_SMALL|  
|136 a 512 K\-8 bytes|UWOP\_ALLOC\_LARGE, información de la operación \= 0|  
|512 K a 4 G\-8 bytes|UWOP\_ALLOC\_LARGE, información de la operación \= 1|  
  
 UWOP\_SET\_FPREG \(3\)1 nodo  
  
 Establecen el registro de puntero de marco configurando el registro con cierto desplazamiento del RSP actual.  El desplazamiento es igual al campo de desplazamiento Frame Register \(con cambio de escala\) en UNWIND\_INFO \* 16, permitiendo desplazamientos de 0 a 240.  El uso de un desplazamiento permite establecer un puntero de marco que apunta al centro de la asignación del espacio fijo de la pila, lo que favorece la densidad del código al permitir más accesos para usar formatos de instrucción cortos.  Observe que el campo de información de la operación está reservado y no se utiliza.  
  
 UWOP\_SAVE\_NONVOL \(4\)2 nodos  
  
 Guardan un registro entero no variable en la pila utilizando MOV en lugar de PUSH.  Esto se utiliza principalmente para ajuste de reducción, donde un registro no variable se guarda en la pila en una posición que se asignó previamente.  La información de la operación es el número del registro.  El desplazamiento de la pila con una escala de 8 aplicada se registra en la siguiente ranura de código de operación de desenredo, como se describe en la nota anterior.  
  
 UWOP\_SAVE\_NONVOL\_FAR \(5\)3 nodos  
  
 Guardan un registro entero no variable en la pila con un desplazamiento largo, utilizando MOV en lugar de PUSH.  Esto se utiliza principalmente para ajuste de reducción, donde un registro no variable se guarda en la pila en una posición que se asignó previamente.  La información de la operación es el número del registro.  El desplazamiento de la pila sin cambio de escala se registra en las dos siguientes ranuras de código de operación de desenredo, como se describe en la nota anterior.  
  
 UWOP\_SAVE\_XMM128 \(8\)2 nodos  
  
 Guardan los 128 bits de un registro XMM no variable en la pila.  La información de la operación es el número del registro.  El desplazamiento de la pila con escala de 16 se registra en la ranura siguiente.  
  
 UWOP\_SAVE\_XMM128\_FAR \(9\)3 nodos  
  
 Guardan los 128 bits de un registro XMM no variable en la pila con un desplazamiento largo.  La información de la operación es el número del registro.  El desplazamiento de la pila sin cambio de escala se registra en las dos ranuras siguientes.  
  
 UWOP\_PUSH\_MACHFRAME \(10\)1 nodo  
  
 Inserta un marco del equipo.  Se utiliza para registrar el efecto de una interrupción del equipo o una excepción.  Hay dos formas.  Si la información de la operación es igual a 0, se ha insertado lo siguiente en la pila:  
  
|||  
|-|-|  
|RSP\+32|SS|  
|RSP\+24|RSP anterior|  
|RSP\+16|EFLAGS|  
|RSP\+8|CS|  
|RSP|RIP|  
  
 Si la información de la operación es igual a 1, lo que se ha insertado es lo siguiente:  
  
|||  
|-|-|  
|RSP\+40|SS|  
|RSP\+32|RSP anterior|  
|RSP\+24|EFLAGS|  
|RSP\+16|CS|  
|RSP\+8|RIP|  
|RSP|Código de error|  
  
 Este código de desenredo siempre aparece en un prólogo ficticio, que en realidad no se ejecuta nunca, sino que aparece antes del punto de entrada real de una rutina de interrupción y sólo sale para proporcionar un lugar para simular la inserción de un marco del equipo.  UWOP\_PUSH\_MACHFRAME registra esa simulación, que indica que el equipo ha hecho conceptualmente lo siguiente:  
  
 Extraer la dirección de devolución de RIP del principio de la pila a *Temp*  
  
 Insertar SS  
  
 Insertar RSP anterior  
  
 Insertar EFLAGS  
  
 Insertar CS  
  
 Insertar *Temp*  
  
 Insertar Código de error \(si la información de la operación es igual a 1\)  
  
 La operación UWOP\_PUSH\_MACHFRAME simulada reduce RSP en 40 \(la información de la operación es igual a 0\) o 48 \(la información de la operación es igual a 1\).  
  
 **Información de la operación**  
 El significado de estos 4 bits depende del código de la operación.  Para codificar un registro de uso general \(entero\), se utiliza la asignación siguiente:  
  
|||  
|-|-|  
|0|RAX|  
|1|RCX|  
|2|RDX|  
|3|RBX|  
|4|RSP|  
|5|RBP|  
|6|RSI|  
|7|RDI|  
|De 8 a 15|R8 to R15|  
  
## Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)