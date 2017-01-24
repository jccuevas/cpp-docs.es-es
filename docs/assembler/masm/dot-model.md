---
title: ".MODEL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".MODEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".MODEL directive"
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .MODEL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Inicializa el modelo de memoria de programa.  
  
## Sintaxis  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### Parámetros  
 `memorymodel`  
 Parámetro requerido que determina el tamaño de los punteros de código y datos.  
  
 `langtype`  
 Parámetro opcional que define las convenciones de llamada y de nomenclatura para los procedimientos y símbolos públicos.  
  
 `stackoption`  
 Parámetro opcional.  
  
 `stackoption`is not used if `memorymodel` is `FLAT`.  
  
 Especificación de `NEARSTACK` agrupa el segmento de pila en un único segmento físico \(`DGROUP`\) junto con los datos.  El registro de segmento de pila \(`SS`\) se supone que mantenga la misma dirección que el registro de segmento de datos \(`DS`\).  `FARSTACK`No agrupar la pila con `DGROUP`; de este modo `SS` no es igual a `DS`.  
  
## Comentarios  
 .`MODEL`no se utiliza en [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
 En la tabla siguiente enumera los posibles valores para cada parámetro al destinado a plataformas de 16 y 32 bits:  
  
|Parámetro|valores de 32 bits|valores de 16 bits \(soporte para el desarrollo de 16 bits anterior\)|  
|---------------|------------------------|---------------------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|No se utiliza|`NEARSTACK`, `FARSTACK`|  
  
## Código  
 ¿Para obtener ejemplos relacionados con MASM, descargar los ejemplos del compilador de [ejemplos de Visual C\+\+ y la documentación relacionada para 2010 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=178749).  
  
 En el ejemplo siguiente se muestra el uso de la `.MODEL` la directiva.  
  
## Ejemplo  
  
```  
; file simple.asm  
; For x86 (32-bit), assemble with debug information:   
;   ml -c -Zi simple.asm  
; For x64 (64-bit), assemble with debug information:   
;   ml64 -c -DX64 -Zi simple.asm  
;  
; In this sample, the 'X64' define excludes source not used   
;  when targeting the x64 architecture  
  
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
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)   
 [¿Ejemplos de Visual C\+\+ y la documentación relacionada para 2010 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=178749)