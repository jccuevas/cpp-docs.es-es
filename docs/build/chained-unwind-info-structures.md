---
title: "Estructuras encadenadas de informaci&#243;n de desenredo | Microsoft Docs"
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
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Estructuras encadenadas de informaci&#243;n de desenredo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si se establece la marca UNW\_FLAG\_CHAININFO, entonces una estructura de información de desenredo será secundaria y el campo compartido de controlador de excepciones\/dirección de información encadenada contiene la información de desenredo principal.  El siguiente código recupera la información de desenredo primaria , suponiendo que `unwindInfo` es la estructura que tiene la marca UNW\_FLAG\_CHAININFO establecida.  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 La información encadenada es útil en dos situaciones.  Primero, se puede utilizar para segmentos de código no contiguos.  Usando la información encadenada puede reducir la cantidad de información de desenredo necesaria, ya que no tiene que duplicar la matriz de códigos de desenredo a partir de la información de desenredo principal.  
  
 También puede usar la información encadenada para agrupar registros variables guardados.  El compilador puede retrasar el guardar algunos registros variables hasta que está fuera del prólogo de entrada de función.  Puede registrar esto disponiendo de información de desenredo principal para la parte de la función delante del código agrupado y luego configurando información encadenada con un tamaño de prólogo distinto de cero, donde los códigos de desenredo de la información encadenada reflejan las veces que se han guardado los registros no variables.  En ese caso, los códigos de desenredo son todos instancias de UWOP\_SAVE\_NONVOL.  No admiten una agrupación que guarda los registros no volátiles mediante una INSERCIÓN o modifica el registro de RSP mediante una asignación de pila fija adicional.  
  
 Un elemento UNWIND\_INFO con UNW\_FLAG\_CHAININFO establecido puede contener una entrada RUNTIME\_FUNCTION cuyo elemento UNWIND\_INFO también tenga UNW\_FLAG\_CHAININFO establecido \(ajuste de reducción múltiple\).  Finalmente, los punteros de la información de desenredo encadenada llegarán a un elemento UNWIND\_INFO con UNW\_FLAG\_CHAININFO no activado; éste es el elemento UNWIND\_INFO principal, que apunta al punto de entrada del procedimiento real.  
  
## Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)