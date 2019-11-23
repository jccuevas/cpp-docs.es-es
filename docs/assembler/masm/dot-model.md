---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: bfc114a6e71c0eb0ae70005c2657871b6c9e9692
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398108"
---
# <a name="model-32-bit-masm"></a>.MODEL (32-bit MASM)

Inicializa el modelo de memoria de programas. (32-bit MASM only.)

## <a name="syntax"></a>Sintaxis

> **.MODEL** *memory-model* ⟦ __,__ *language-type*⟧ ⟦ __,__ *stack-option*⟧

### <a name="parameters"></a>Parámetros

*memory-model*\
Parámetro necesario que determina el tamaño de los punteros de código y de datos.

*language-type*\
Parámetro opcional que establece las convenciones de llamada y nomenclatura para los procedimientos y los símbolos públicos.

*stack-option*\
Parámetro opcional.

*stack-option* is not used if *memory-model* is **FLAT**.

Specifying **NEARSTACK** groups the stack segment into a single physical segment (**DGROUP**) along with data. The stack segment register (**SS**) is assumed to hold the same address as the data segment register (**DS**). **FARSTACK** does not group the stack with **DGROUP**; thus **SS** does not equal **DS**.

## <a name="remarks"></a>Comentarios

**.MODEL** is not used in [MASM for x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

En la tabla siguiente se enumeran los valores posibles para cada parámetro cuando tenga como destino plataformas de 16 y 32 bits:

|Parámetro|Valores de 32 bits|Valores de 16 bits (compatibilidad con el desarrollo de 16 bits anterior)|
|---------------|--------------------|----------------------------------------------------------------|
|*memory-model*|**FLAT**|**TINY**, **SMALL**, **COMPACT**, **MEDIUM**, **LARGE**, **HUGE**, **FLAT**|
|*language-type*|**C**, **STDCALL**|**C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**|
|*stack-option*|No se utiliza|**NEARSTACK**, **FARSTACK**|

## <a name="code"></a>Código

Para obtener ejemplos relacionados con MASM, descargue los ejemplos del compilador de [Ejemplos de Visual C++ y documentación relacionada de Visual Studio 2010](https://go.microsoft.com/fwlink/p/?linkid=178749).

En el siguiente ejemplo se muestra el uso de la directiva `.MODEL`.

## <a name="example"></a>Ejemplo

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
