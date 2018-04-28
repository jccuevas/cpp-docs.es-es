---
title: . MODELO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2814b1b6cc4483807f77989ff4fbb70929400d6e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="model"></a>.MODEL
Inicializa el modelo de memoria de programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memorymodel`  
 Parámetro necesario que determina el tamaño de los punteros de código y los datos.  
  
 `langtype`  
 Parámetro opcional que establece las convenciones de llamada y nomenclaturas para los procedimientos y los símbolos públicos.  
  
 `stackoption`  
 Parámetro opcional.  
  
 `stackoption` no se utiliza si `memorymodel` es `FLAT`.  
  
 Especificar `NEARSTACK` agrupa el segmento de pila en un único segmento físico (`DGROUP`) junto con los datos. El registro de segmento de pila (`SS`) se supone que mantenga la misma dirección que el registro de segmento de datos (`DS`). `FARSTACK` no se agrupan la pila con `DGROUP`; por lo tanto `SS` no es igual a `DS`.  
  
## <a name="remarks"></a>Comentarios  
 .`MODEL` no se utiliza en [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
 En la tabla siguiente se enumera los posibles valores para cada parámetro al elegir como destino plataformas de 16 bits y 32 bits:  
  
|Parámetro|valores de 32 bits|valores de 16 bits (compatibilidad con el desarrollo de 16 bits anterior)|  
|---------------|--------------------|----------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|No se utiliza|`NEARSTACK`, `FARSTACK`|  
  
## <a name="code"></a>Código  
 Para consultar ejemplos relacionados con MASM, descargue las muestras del compilador de [ejemplos de Visual C++ y la documentación relacionada para Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).  
  
 En el ejemplo siguiente se muestra el uso de la `.MODEL` directiva.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
 [Ejemplos de Visual C++ y la documentación relacionada para Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)