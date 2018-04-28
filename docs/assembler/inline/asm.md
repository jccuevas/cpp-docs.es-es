---
title: __asm | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- __asm
- __asm_cpp
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77e09f6af92839c6113c9c5ba375a1583bcf7149
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="asm"></a>__asm
**Específicos de Microsoft**  
  
 La palabra clave `__asm` invoca el ensamblador alineado y puede aparecer siempre que una instrucción de C o C++ sea válida. No puede aparecer por sí sola. Debe ir seguida de una instrucción de ensamblado, un grupo de instrucciones entre llaves o, como mínimo, un par de llaves vacío. El término "bloque `__asm`" aquí hace referencia a cualquier instrucción o grupo de instrucciones, incluido o no entre llaves.  
  
> [!NOTE]
>  La compatibilidad de Visual C++ con la palabra clave `asm` de C++ estándar se limita al hecho de que el compilador no generará un error en la palabra clave. Sin embargo, un bloque `asm` no generará ningún código importante. Use `__asm` en lugar de `asm`.  
  
 Sintaxis:  
  
 __asm *instrucción de ensamblado* [;]  
  
 __asm { *lista de instrucciones de ensamblado* } [;]  
  
## <a name="grammar"></a>Gramática  
 `__asm`  `assembly-instruction`  `;`participación  
  
 `__asm {`  `assembly-instruction-list`  `};`participación  
  
 *lista de instrucciones de ensamblado*:  
 `assembly-instruction` `;`participación  
  
 `assembly-instruction` `;` `assembly-instruction-list` `;`participación  
  
 Si se utiliza sin llaves, la palabra clave `__asm` indica que el resto de la línea es una instrucción de lenguaje de ensamblado. Si se utiliza con llaves, indica que cada línea entre las llaves es una instrucción de lenguaje de ensamblado. Por compatibilidad con versiones anteriores, `_asm` es un sinónimo de `__asm`.  
  
 Dado que la palabra clave `__asm` es un separador de la instrucción, puede colocar las instrucciones de ensamblado en la misma línea.  
  
 Antes de Visual C++ 2005, la instrucción  
  
```  
__asm int 3  
```  
  
 no se ha originado el código nativo que se genera cuando se compila con **/CLR**; el compilador traducía la instrucción a una instrucción de interrupción CLR.  
  
 `__asm int 3` ahora da lugar a la generación de código nativo para la función. Si desea que una función para hacer que un punto de interrupción en el código y si desea que esa función compilada en MSIL, use [__debugbreak](../../intrinsics/debugbreak.md).  
  
## <a name="example"></a>Ejemplo  
 El fragmento de código siguiente es un bloque `__asm` simple incluido entre llaves:  
  
```  
__asm {  
   mov al, 2  
   mov dx, 0xD007  
   out dx, al  
}  
```  
  
 Como alternativa, puede colocar `__asm` delante de cada instrucción de ensamblado:  
  
```  
__asm mov al, 2  
__asm mov dx, 0xD007  
__asm out dx, al  
```  
  
 Debido a que la palabra clave `__asm` es un separador de la instrucción, también puede colocar las instrucciones de ensamblado en la misma línea.  
  
```  
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al  
```  
  
 Los tres ejemplos generan el mismo código, pero el primer estilo (incluyendo el bloque `__asm` entre llaves) tiene algunas ventajas. Las llaves separan claramente el código de ensamblado del código de C o C++ y evitan la repetición innecesaria de la palabra clave `__asm`. Las llaves también pueden evitar ambigüedades. Si desea colocar una instrucción de C o C++ en la misma línea que un bloque `__asm`, debe incluir el bloque entre llaves. Sin las llaves, el compilador no puede indicar dónde se detiene el código de ensamblado y dónde comienzan las instrucciones de C o C++. Finalmente, como el texto entre llaves tiene el mismo formato que el texto de MASM normal, se puede cortar y pegar fácilmente el texto de los archivos de código fuente de MASM existentes.  
  
 A diferencia de las llaves en C y C++, las llaves que incluyen un bloque `__asm` no afectan al ámbito de las variables. También puede anidar los bloques `__asm`; el anidado no afecta al ámbito de las variables.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../../cpp/keywords-cpp.md)   
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)