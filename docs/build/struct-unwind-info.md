---
title: "UNWIND_INFO (Estructura) | Microsoft Docs"
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
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# UNWIND_INFO (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El struct de la información de datos de desenredo sirve para registrar el efecto de una función en el puntero de la pila y el lugar donde se guardan los registros no variables en la pila:  
  
|||  
|-|-|  
|UBYTE: 3|Versión|  
|UBYTE: 5|Marcadores|  
|UBYTE|Tamaño de prólogo|  
|UBYTE|Recuento de códigos de desenredo|  
|UBYTE: 4|Registro de marco|  
|UBYTE: 4|Desplazamiento \(con cambio de escala\) de registro de marco|  
|USHORT \* n|Matriz de códigos de desenredo|  
|variable|Puede ser de la forma \(1\) o \(2\) según se indica a continuación|  
  
 \(1\) Controlador de excepciones  
  
|||  
|-|-|  
|ULONG|Dirección del controlador de excepciones|  
|variable|Datos del controlador específicos del lenguaje \(opcional\)|  
  
 \(2\) Encadenado desenredo información  
  
|||  
|-|-|  
|ULONG|Dirección de inicio de la función|  
|ULONG|Dirección de fin de la función|  
|ULONG|Dirección de información de desenredo|  
  
 El struct UNWIND\_INFO debe tener alineación DWORD en memoria.  El significado de cada campo es el siguiente:  
  
 **Versión**  
 El número de versión de los datos de desenredo, actualmente 1.  
  
 **Marcadores**  
 Se definen tres marcadores actualmente:  
  
 La función de UNW\_FLAG\_EHANDLER The tiene un controlador de excepciones que debe llamar al buscar funciona la necesidad de examinar excepciones.  
  
 La función de UNW\_FLAG\_UHANDLER The tiene un controlador de terminación que debe llamar al desenredo una excepción.  
  
 UNW\_FLAG\_CHAININFO This desenreda la estructura de información no es el principal del procedimiento.  En su lugar, la entrada de información de desenredo encadenada es el contenido de una entrada RUNTIME\_FUNCTION anterior.  El texto siguiente es una explicación de las estructuras de información de desenredo encadenada.  Si se establece este marcador, se deben desactivar los marcadores UNW\_FLAG\_EHANDLER y UNW\_FLAG\_UHANDLER.  Además, el registro del marco y los campos de asignación del espacio fijo de la pila deben tener los mismos valores que en la información principal de desenredo.  
  
 **Tamaño de prólogo**  
 Longitud del prólogo de la función en bytes.  
  
 **Recuento de códigos de desenredo**  
 Es el número de ranuras en la matriz de códigos de desenredo.  Tenga en cuenta que algunos códigos de desenredo \(por ejemplo, UWOP\_SAVE\_NONVOL\) requieren más de una ranura en la matriz.  
  
 **Registro de marco**  
 Si es distinto de cero, la función utiliza un puntero de marco y este campo es el número del registro no variable empleado como puntero de marco, con la misma codificación para el campo de información de la operación de los nodos UNWIND\_CODE.  
  
 **Desplazamiento \(con cambio de escala\) de registro de marco**  
 Si el campo de registro de marco es distinto de cero, se trata del desplazamiento con cambio de escala desde RSP que se aplica al registro de FP cuando se establece.  El registro de FP real se establece en RSP \+ 16 \* este número, permitiendo desplazamientos de 0 a 240.  Así, se puede apuntar el registro de FP al centro de la asignación local de la pila para marcos de pila dinámicos, lo que permite una mejor densidad del código por el uso de instrucciones más breves \(más instrucciones pueden usar el formato de desplazamiento de 8 bits con signo\).  
  
 **Matriz de códigos de desenredo**  
 Se trata de una matriz de elementos que explica el efecto del prólogo en los registros no variables y RSP.  Vea la sección sobre UNWIND\_CODE para conocer los significados de elementos individuales.  Para la alineación, esta matriz siempre tendrá un número impar de entradas, con la última potencialmente sin utilizar \(en cuyo caso, la matriz tendrá una longitud que superará en uno la indicada en el campo de recuento de códigos de desenredo\).  
  
 **Dirección del controlador de excepciones**  
 Es un puntero relativo a una imagen, al controlador de terminación o de excepciones específico del lenguaje de la función \(si el marcador UNW\_FLAG\_CHAININFO está desactivado y se ha establecido uno de los marcadores UNW\_FLAG\_EHANDLER o UNW\_FLAG\_UHANDLER\).  
  
 **Datos del controlador específicos del lenguaje**  
 Son los datos del controlador de excepciones específicos del lenguaje de la función.  El formato de estos datos no está especificado y está determinado completamente por el controlador de excepciones que se utilice.  
  
 **Información de desenredo encadenada**  
 Si se establece el marcador UNW\_FLAG\_CHAININFO, el struct UNWIND\_INFO finaliza con tres UWORD.  Estos UWORD representan la información de RUNTIME\_FUNCTION correspondiente a la función de la información de desenredo encadenada.  
  
## Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)