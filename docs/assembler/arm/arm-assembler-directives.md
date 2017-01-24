---
title: "ARM Assembler Directives | Microsoft Docs"
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
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ARM Assembler Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En su mayor parte, el ensamblador de ARM de Microsoft utiliza el lenguaje de ensamblado de ARM, que se documenta en el capítulo 7 de la [manual de herramientas de ensamblador de ARM](http://go.microsoft.com/fwlink/?LinkId=246102).  Sin embargo, las implementaciones de Microsoft de algunas directivas de ensamblado difieren de las directivas de ensamblado del ARM.  En este artículo se explica las diferencias.  
  
## Implementaciones de Microsoft de las directivas de ensamblado de ARM  
 ÁREA  
 El ensamblador de ARM de Microsoft es compatible con estos atributos de zona: alinear, código, CODEALIGN, datos, NOINIT, READONLY, READWRITE, PULGAR, ARM.  
  
 Todas excepto THUMB y ARM funcionan tal como se documenta en el [manual de herramientas de ensamblador de ARM](http://go.microsoft.com/fwlink/?LinkId=246102).  
  
 En el ensamblador Microsoft ARM THUMB indica que una sección de código contiene código de control de posición y es el valor predeterminado para las secciones de código.  ARM indica que la sección contiene código ARM.  
  
 ATTR  
 No se admite.  
  
 CODE16  
 No se admite porque implica la sintaxis de pulgar pre\-UAL, que no se admite el ensamblador de ARM de Microsoft.  Utilice la directiva de control de posición en su lugar, junto con la sintaxis de United Airlines.  
  
 COMÚN  
 No se admite la especificación de una alineación para la región común.  
  
 DCDO  
 No se admite.  
  
 DN, QN, SN  
 No se admite la especificación de un tipo o un carril en el alias de registro.  
  
 ENTRADA  
 No se admite.  
  
 EQU  
 No se admite la especificación de un tipo para el símbolo definido.  
  
 EXPORTACIÓN y GLOBAL  
 ```  
  
EXPORTsym {[type]}  
  
```  
  
 `sym`es el símbolo que se va a exportar.  `[type]`, si se especifica, puede ser una `[DATA]` para indicar que el símbolo de puntos de datos o `[FUNC]` para indicar que el símbolo hace referencia al código.  
  
 GLOBAL es un sinónimo para la exportación.  
  
 EXPORTAS  
 No se admite.  
  
 MARCO  
 No se admite.  
  
 FUNCIÓN y PROC  
 Aunque la sintaxis de ensamblado es compatible con la especificación de una costumbre convención de llamada a procedimientos con una lista de los registros que son Guardar llamador y aquellos que son el ahorro de destinatario de la llamada, el ensamblador de ARM de Microsoft acepta la sintaxis pero pasa por alto las listas de registro.  La información de depuración que se produce por el ensamblador admite únicamente la convención de llamada de la predeterminada.  
  
 IMPORTACIÓN y EXTERN  
 ```  
  
IMPORT sym{, WEAK alias{, TYPE t}}  
  
```  
  
 `sym`es el nombre del símbolo que desea importar.  
  
 Si DÉBIL `alias` se especifica, indica que `sym` es un externo débil.  Si no hay definición para el se encuentra en tiempo de vinculación, a continuación, todas las referencias a ella en su lugar enlazar a `alias`.  
  
 Si tipo de  `t` se especifica, a continuación, `t` indica cómo el vinculador debe intentar resolver `sym`.  Estos valores para `t` son posibles:   
1: Realizar una búsqueda de la biblioteca de`sym`   
2: Realizar una búsqueda de la biblioteca de`sym`   
3 —`sym` es un alias de `alias` \(predeterminado\)  
  
 EXTERN es un sinónimo para la importación, salvo que `sym` se importa sólo si hay referencias a él en el ensamblado actual.  
  
 MACRO  
 No se admite el uso de una variable para contener el código de condición de una macro.  Los valores para la macro no se admiten parámetros predeterminados.  
  
 NOFP  
 No se admite.  
  
 OPT, TTL, SUBT  
 No se admite porque el ensamblador de ARM de Microsoft no produce anuncios.  
  
 PRESERVE8  
 No se admite.  
  
 RELOC  
 `RELOC n`sólo se puede seguir una instrucción o una directiva de definición de datos.  No hay ningún "símbolo anónimo" que puede ser reubicado.  
  
 REQUIEREN  
 No se admite.  
  
 REQUIRE8  
 No se admite.  
  
 THUMBX  
 No se admite porque el ensamblador de ARM de Microsoft no admite el conjunto de instrucciones de control de posición 2EE.  
  
## Vea también  
 [ARM Assembler Command\-Line Reference](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM Assembler Diagnostic Messages](../../assembler/arm/arm-assembler-diagnostic-messages.md)