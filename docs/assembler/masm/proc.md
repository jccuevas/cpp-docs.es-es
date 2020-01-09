---
title: PROC
ms.date: 12/06/2019
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: 85d9a1e82eebcd83cb0f12f5ca751ec9415af18d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318675"
---
# <a name="proc"></a>PROC

Marca el inicio y el final de un bloque de procedimiento denominado *etiqueta*. Las instrucciones del bloque se pueden llamar con la instrucción **Call** o la directiva [INVOKE](invoke.md) .

## <a name="syntax"></a>Sintaxis

> *Label* **proc** ⟦*Distance*⟧ ⟦*Language-Type*⟧ ⟦ **Public** | **Private** | **Export** ⟧ ⟦ __\<__ *prologuearg* __>__ ⟧ ⟦**usa** *reglist*⟧ ⟦ __,__ *parámetro* ⟦ __:__ *Tag*⟧... ⟧\
> ⟦**Frame** ⟦ __:__ *ehandler-Address*⟧ ⟧ \
> *instrucciones*\
> *etiqueta* **ENDP**

## <a name="remarks"></a>Notas

Los argumentos ⟦*Distance*⟧ y ⟦*Language-Type*⟧ solo son válidos en MASM de 32 bits.

⟦**Frame** ⟦ __:__ *ehandler-Address*⟧ ⟧ solo es válido con ml64. exe y hace que MASM genere una entrada de tabla de función en. pdata e información de desenredado en. xdata para el comportamiento de desenredado de la excepción estructurada de una función.

Cuando se usa el atributo de **marco** , debe ir seguido de un [. Directiva ENDPROLOG](dot-endprolog.md) .

Consulte [MASM para x64 (ml64. exe)](masm-for-x64-ml64-exe.md) para obtener más información sobre el uso de ml64. exe.

## <a name="example"></a>Ejemplo

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

El código anterior emitirá la siguiente tabla de funciones y la información de desenredo:

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
