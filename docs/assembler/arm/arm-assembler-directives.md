---
title: Directivas del ensamblador de ARM | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 282d8bbd55bec8053961c709eb3733a65972b187
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693118"
---
# <a name="arm-assembler-directives"></a>Directiva del ensamblador de ARM

En su mayor parte, el ensamblador de ARM Microsoft utiliza el lenguaje ensamblador ARM, que se documenta en el [Guía de referencia del compilador ARM armasm](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html). Sin embargo, las implementaciones de Microsoft de algunas directivas de ensamblado diferencian de las directivas de ensamblado ARM. En este artículo se explica las diferencias.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementaciones de Microsoft de las directivas de ensamblado ARM

`AREA`<br/>
El ensamblador de ARM Microsoft es compatible con estos `AREA` atributos: `ALIGN`, `CODE`, `CODEALIGN`, `DATA`, `NOINIT`, `READONLY`, `READWRITE`, `THUMB`, `ARM`.

Todos excepto `THUMB` y `ARM` funcionan como se documenta en el [Guía de referencia del compilador ARM armasm](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

En el ensamblador de ARM Microsoft `THUMB` indica que un `CODE` sección contiene código Thumb y es el valor predeterminado para `CODE` secciones.  `ARM` indica que la sección contiene código ARM.

`ATTR`<br/>
No se admite.

`CODE16`<br/>
No se admite porque implica la sintaxis de Thumb pre-UAL, que no se permite el ensamblador de ARM Microsoft.  Use el `THUMB` la directiva en su lugar, junto con la sintaxis de UAL.

`COMMON`<br/>
No se admite la especificación de una alineación de la región comunes.

`DCDO`<br/>
No se admite.

`DN`, `QN`, `SN`<br/>
No se admite la especificación de un tipo o una calle en el registro de alias.

`ENTRY`<br/>
No se admite.

`EQU`<br/>
No se admite la especificación de un tipo para el símbolo definido.

`EXPORT` y `GLOBAL`

> **EXPORTAR** <em>sym</em>{**[**<em>tipo</em>**]**}

*SYM* es el símbolo que se exportarán.  [*tipo*], si se especifica, puede ser `[DATA]` para indicar que el símbolo apunta a datos o `[FUNC]` para indicar que el símbolo apunta al código.

`GLOBAL` es un sinónimo de `EXPORT`.

`EXPORTAS`<br/>
No se admite.

`FRAME`<br/>
No se admite.

`FUNCTION` y `PROC`<br/>
Aunque la sintaxis de ensamblado es compatible con la especificación de un personalizado convención de llamada en los procedimientos con una lista de los registros que están llamador guardado y los que guardar de destinatario, el ensamblador de ARM Microsoft acepta la sintaxis, pero omite las listas de registro.  La información de depuración generada por el ensamblador admite solo la convención de llamada predeterminada.

`IMPORT` y `EXTERN`

> **IMPORTACIÓN** *sym*{**, DÉBIL** *alias*{**, tipo** *t*}}

*SYM* es el nombre del símbolo que desea importar.

Si `WEAK` *alias* se especifica, indica que *sym* es un externo débil. Si se encuentra ninguna definición para él en tiempo de vinculación, todas las referencias a él en su lugar, enlazar a *alias*.

Si `TYPE` *t* se especifica, a continuación, *t* indica cómo el vinculador debe intentar resolver *sym*.  Estos valores para *t* son posibles:<br/>
1: no lleva a cabo una búsqueda de biblioteca de *sym*<br/>
2: realizar una búsqueda de biblioteca de *sym*<br/>
3:*sym* es un alias para *alias* (valor predeterminado)

`EXTERN` es un sinónimo de `IMPORT`, salvo que *sym* se importan solo si hay referencias a él en el ensamblado actual.

`MACRO`<br/>
No se admite el uso de una variable que contenga el código de la condición de una macro. Los valores de macro no se admiten parámetros predeterminados.

`NOFP`<br/>
No se admite.

`OPT`, `TTL`, `SUBT`<br/>
No se admite porque el ensamblador de ARM Microsoft no genera anuncios.

`PRESERVE8`<br/>
No se admite.

`RELOC`<br/>
`RELOC n` solo se puede seguir una instrucción o una directiva de la definición de datos. No hay ningún "anónimo"symbol"que se puede reasignar.

`REQUIRE`<br/>
No se admite.

`REQUIRE8`<br/>
No se admite.

`THUMBX`<br/>
No se admite porque el ensamblador de ARM Microsoft no admite el conjunto de instrucciones de Thumb 2EE.

## <a name="see-also"></a>Vea también

[Referencia de la línea de comandos del ensamblador de ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Mensajes de diagnóstico del ensamblador de ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
