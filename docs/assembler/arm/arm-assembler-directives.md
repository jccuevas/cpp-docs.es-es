---
title: Directiva del ensamblador de ARM
ms.date: 08/30/2018
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
ms.openlocfilehash: 9124f893b3334e0893073332c9d5f5a1388373d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167678"
---
# <a name="arm-assembler-directives"></a>Directiva del ensamblador de ARM

En su mayor parte, el ensamblador de ARM Microsoft utiliza el lenguaje ensamblador ARM, que se documenta en el [Guía de referencia del compilador ARM armasm](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Sin embargo, las implementaciones de Microsoft de algunas directivas de ensamblado diferencian de las directivas de ensamblado ARM. En este artículo se explica las diferencias.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementaciones de Microsoft de las directivas de ensamblado ARM

- ÁREA

   El ensamblador de ARM Microsoft es compatible con estos `AREA` atributos: `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

   Todos excepto `THUMB` y `ARM` funcionan como se documenta en el [Guía de referencia del compilador ARM armasm](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

   En el ensamblador de ARM Microsoft `THUMB` indica que un `CODE` sección contiene código Thumb y es el valor predeterminado para `CODE` secciones.  `ARM` indica que la sección contiene código ARM.

- ATTR

   No se admite.

- CODE16

   No se admite porque implica la sintaxis de Thumb pre-UAL, que no se permite el ensamblador de ARM Microsoft.  Use el `THUMB` la directiva en su lugar, junto con la sintaxis de UAL.

- COMUNES

   No se admite la especificación de una alineación de la región comunes.

- DCDO

   No se admite.

- `DN`, `QN`, `SN`

   No se admite la especificación de un tipo o una calle en el registro de alias.

- ENTRADA

   No se admite.

- EQU

   No se admite la especificación de un tipo para el símbolo definido.

- `EXPORT` y `GLOBAL`

   Especifica las exportaciones con esta sintaxis:

   > **EXPORTAR**|**GLOBAL** <em>sym</em>{**[**<em>tipo</em>**]**}

   *SYM* es el símbolo que se exportarán.  [*tipo*], si se especifica, puede ser `[DATA]` para indicar que el símbolo apunta a datos o `[FUNC]` para indicar que el símbolo apunta al código. `GLOBAL` es un sinónimo de `EXPORT`.

- EXPORTAS

   No se admite.

- MARCO

   No se admite.

- `FUNCTION` y `PROC`

   Aunque la sintaxis de ensamblado es compatible con la especificación de un personalizado convención de llamada en los procedimientos con una lista de los registros que están llamador guardado y los que guardar de destinatario, el ensamblador de ARM Microsoft acepta la sintaxis, pero omite las listas de registro.  La información de depuración generada por el ensamblador admite solo la convención de llamada predeterminada.

- `IMPORT` y `EXTERN`

   Especifica las importaciones con esta sintaxis:

   > **IMPORTACIÓN**|**EXTERN** *sym*{**, DÉBIL** *alias*{**, tipo** *t*}}

   *SYM* es el nombre del símbolo que desea importar.

   Si `WEAK` *alias* se especifica, indica que *sym* es un externo débil. Si se encuentra ninguna definición para él en tiempo de vinculación, todas las referencias a él en su lugar, enlazar a *alias*.

   Si `TYPE` *t* se especifica, a continuación, *t* indica cómo el vinculador debe intentar resolver *sym*.  Estos valores para *t* son posibles:

   |Valor|Descripción|
   |-|-|
   |1|No lleva a cabo una búsqueda de biblioteca de *sym*|
   |2|Realizar una búsqueda de biblioteca de *sym*|
   |3|*SYM* es un alias para *alias* (valor predeterminado)|

   `EXTERN` es un sinónimo de `IMPORT`, salvo que *sym* se importan solo si hay referencias a él en el ensamblado actual.

- MACRO

   No se admite el uso de una variable que contenga el código de la condición de una macro. Los valores de macro no se admiten parámetros predeterminados.

- NOFP

   No se admite.

- `OPT`, `TTL`, `SUBT`

   No se admite porque el ensamblador de ARM Microsoft no genera anuncios.

- PRESERVE8

   No se admite.

- RELOC

   `RELOC n` solo se puede seguir una instrucción o una directiva de la definición de datos. No hay ningún "anónimo"symbol"que se puede reasignar.

- REQUERIR

   No se admite.

- REQUIRE8

   No se admite.

- THUMBX

   No se admite porque el ensamblador de ARM Microsoft no admite el conjunto de instrucciones de Thumb 2EE.

## <a name="see-also"></a>Vea también

[Referencia de la línea de comandos del ensamblador de ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Mensajes de diagnóstico del ensamblador de ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
