---
title: Directiva del ensamblador de ARM | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5ab97fb9ccdff19206b829383c622efd3f7921
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053306"
---
# <a name="arm-assembler-directives"></a>Directiva del ensamblador de ARM
En su mayor parte, el ensamblador de ARM de Microsoft usa el lenguaje de ensamblador ARM, que se describe en el capítulo 7 de la [Guía de herramientas de ensamblador de ARM](http://go.microsoft.com/fwlink/p/?linkid=246102). Sin embargo, las implementaciones de Microsoft de algunas directivas de ensamblado diferencian de las directivas de ensamblado ARM. En este artículo se explica las diferencias.  
  
## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementaciones de directivas de ensamblado ARM Microsoft  
 ÁREA  
 El ensamblador de ARM de Microsoft es compatible con estos atributos de área: alinear código, CODEALIGN, datos, NOINIT, solo lectura, lectura y escritura, THUMB, ARM.  
  
 Todas excepto THUMB y ARM funcionan como se documenta en la [Guía de herramientas de ensamblador de ARM](http://go.microsoft.com/fwlink/p/?linkid=246102).  
  
 En el ensamblador de ARM de Microsoft, THUMB indica que una sección de código contiene código Thumb y es el valor predeterminado para las secciones de código.  ARM indica que la sección contiene código ARM.  
  
 ATTR  
 No se admite.  
  
 CODE16  
 No se admite porque implica la sintaxis de Thumb pre-UAL, que no permite que el ensamblador de ARM de Microsoft.  Utilice la directiva de control de posición en su lugar, junto con la sintaxis UAL.  
  
 COMUNES  
 No se admite la especificación de una alineación de la región comunes.  
  
 DCDO  
 No se admite.  
  
 DN, QN, SN  
 No se admite la especificación de un tipo o una calle en el registro de alias.  
  
 ENTRADA  
 No se admite.  
  
 EQU  
 No se admite la especificación de un tipo para el símbolo definido.  
  
 EXPORTACIÓN y GLOBAL  
 ```  
EXPORTsym {[type]}  
```  
  
 `sym` es el símbolo que se exportarán.  `[type]`, si se especifica, puede ser `[DATA]` para indicar que el símbolo apunta a los datos o `[FUNC]` para indicar que el símbolo hace referencia al código.  
  
 GLOBAL es un sinónimo para la exportación.  
  
 EXPORTAS  
 No se admite.  
  
 MARCO  
 No se admite.  
  
 FUNCIÓN y PROC  
 Aunque la sintaxis de ensamblado es compatible con la especificación de un personalizado convención de llamada en los procedimientos con una lista de los registros que están llamador guardado y los que están destinatario guardado, el ensamblador de ARM de Microsoft acepta la sintaxis pero omite las listas de registro.  La información de depuración generada por el ensamblador admite solo la convención de llamada predeterminada.  
  
 IMPORTACIÓN y EXTERN  
 ```  
IMPORT sym{, WEAK alias{, TYPE t}}  
```  
  
 `sym` es el nombre del símbolo que desea importar.  
  
 Si DÉBIL `alias` se especifica, indica que `sym` es un external débil. Si se encuentra ninguna definición para ella en tiempo de vinculación, todas las referencias a ella en su lugar, enlazar a `alias`.  
  
 Si tipo `t` no se especifica, `t` indica cómo el vinculador debería intentar resolver `sym`.  Estos valores para `t` son posibles:   
1: no se realice una búsqueda de la biblioteca de `sym`  
2: realizar una búsqueda de la biblioteca de `sym`  
3:`sym` es un alias para `alias` (valor predeterminado)  
  
 EXTERN es un sinónimo para la importación, salvo que `sym` se importan solo si hay referencias a él en el ensamblado actual.  
  
 MACRO  
 No se admite el uso de una variable que contenga el código de la condición de una macro. Valores predeterminados de la macro no se admiten parámetros.  
  
 NOFP  
 No se admite.  
  
 PARTICIPACIÓN, TTL, SUBT  
 No se admite porque el ensamblador de ARM de Microsoft no genera la lista de programas.  
  
 PRESERVE8  
 No se admite.  
  
 REUBIQUE  
 `RELOC n` solo se puede seguir una instrucción o una directiva de definición de datos. No hay ninguna "anónimo"symbol"que se puede reasignar.  
  
 REQUERIR  
 No se admite.  
  
 REQUIRE8  
 No se admite.  
  
 THUMBX  
 No se admite porque el ensamblador de ARM de Microsoft no admite el conjunto de instrucciones de Thumb-2EE.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de línea de comandos de ensamblador ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Mensajes de diagnóstico del ensamblador de ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)