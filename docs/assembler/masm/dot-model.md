---
title: . MODELO | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .MODEL
dev_langs:
- C++
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2b9606fc849658181cda5067f396a270f0ee3bb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678175"
---
# <a name="model"></a>.MODEL

Inicializa el modelo de memoria de programa.

## <a name="syntax"></a>Sintaxis

> . MODELO memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>Parámetros

*memorymodel*<br/>
Parámetro necesario que determina el tamaño de los punteros de código y los datos.

*langtype*<br/>
Parámetro opcional que establece las convenciones de llamada y nomenclatura para los procedimientos y los símbolos públicos.

*stackoption*<br/>
Parámetro opcional.

*stackoption* no se utiliza si *memorymodel* es `FLAT`.

Especificar `NEARSTACK` agrupa el segmento de pila en un único segmento físico (`DGROUP`) junto con los datos. El registro de segmento de pila (`SS`) se supone que mantenga la misma dirección que el registro de segmento de datos (`DS`). `FARSTACK` no se agrupa la pila con `DGROUP`; por lo tanto `SS` no es igual a `DS`.

## <a name="remarks"></a>Comentarios

.`MODEL` no se usa en [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

En la tabla siguiente se enumera los valores posibles para cada parámetro cuando tenga como destino plataformas de 16 bits y 32 bits:

|Parámetro|valores de 32 bits|valores de 16 bits (compatibilidad para el desarrollo de 16 bits anterior)|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|No se utiliza|`NEARSTACK`, `FARSTACK`|

## <a name="code"></a>Código

Para obtener ejemplos relacionados con MASM, descargar los ejemplos del compilador desde [ejemplos de Visual C++ y la documentación relacionada para Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).

En el ejemplo siguiente se muestra el uso de la `.MODEL` directiva.

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

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>

