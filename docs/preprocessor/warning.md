---
title: "warning | Microsoft Docs"
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
  - "warning_CPP"
  - "vc-pragma.warning"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "pop warning (pragma)"
  - "pragma (directivas), warning"
  - "push pragma warning"
  - "warning (pragma)"
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# warning
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Habilita la modificación selectiva del comportamiento de los mensajes de advertencia del compilador.  
  
## Sintaxis  
  
```  
  
      #pragma warning(   
      warning-specifier  
       :   
      warning-number-list [; warning-specifier : warning-number-list...] )  
#pragma warning( push[ ,n ] )  
#pragma warning( pop )  
```  
  
## Comentarios  
 Los siguientes parámetros de warning\-specifier están disponibles.  
  
|warning\-specifier|Significado|  
|------------------------|-----------------|  
|`1, 2, 3, 4`|Aplica el nivel dado a las advertencias especificadas.  También activa una advertencia especificada que está desactivada de forma predeterminada.|  
|`default`|Restablece el comportamiento de advertencia a su valor predeterminado.  También activa una advertencia especificada que está desactivada de forma predeterminada.  La advertencia se generará en su nivel predeterminado documentado.<br /><br /> Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../preprocessor/compiler-warnings-that-are-off-by-default.md).|  
|`disable`|No emite los mensajes de advertencia especificados.|  
|`error`|Notifica las advertencias especificadas como errores.|  
|`once`|Muestra los mensajes especificados solo una vez.|  
|`suppress`|Inserta el estado actual de la pragma en la pila, deshabilita la advertencia especificada para la línea siguiente y, a continuación, extrae de la pila la advertencia para que se restablezca el estado de pragma.|  
  
 En la instrucción de código siguiente se muestra que un parámetro `warning-number-list` puede contener varios números de advertencia, y que se pueden especificar varios parámetros `warning-specifier` en la misma directiva pragma.  
  
```  
#pragma warning( disable : 4507 34; once : 4385; error : 164 )  
```  
  
 Este es el equivalente funcional del código siguiente.  
  
```  
// Disable warning messages 4507 and 4034.  
#pragma warning( disable : 4507 34 )  
  
// Issue warning 4385 only once.  
#pragma warning( once : 4385 )  
  
// Report warning 4164 as an error.  
#pragma warning( error : 164 )  
```  
  
 El compilador agrega 4000 a cualquier número de advertencia que esté entre 0 y 999.  
  
 Para los números de advertencia en el intervalo 4700 \- 4999, que son los asociados a la generación de código, el estado de la advertencia en vigor cuando el compilador encuentra la llave de apertura de una función estará en vigor para el resto de la función.  El uso de la pragma `warning` en la función para cambiar el estado de una advertencia que tiene un número superior a 4699 solo tendrá efecto después del final de la función.  En el ejemplo siguiente se muestra la colocación correcta de pragmas `warning` para deshabilitar un mensaje de advertencia de generación de código y restaurarlo a continuación.  
  
```  
// pragma_warning.cpp  
// compile with: /W1  
#pragma warning(disable:4700)  
void Test() {  
   int x;  
   int y = x;   // no C4700 here  
   #pragma warning(default:4700)   // C4700 enabled after Test ends  
}  
  
int main() {  
   int x;  
   int y = x;   // C4700  
}  
```  
  
 Observe que en el cuerpo de la función, el último valor de la pragma `warning` entrará en vigor para la función completa.  
  
## Inserción y extracción  
 La pragma `warning` también admite la sintaxis siguiente.  
  
 `#pragma warning(` `push` \[ `,``n` \] `)`  
  
 `#pragma warning(` `pop )`  
  
 Donde `n` representa un nivel de advertencia \(1 a 4\).  
  
 La pragma `warning( push )` almacena el estado de advertencia actual para cada advertencia.  La pragma `warning( push,` `n``)` almacena el estado actual para cada advertencia y establece el nivel de advertencia global en `n`.  
  
 La pragma `warning( pop )` extrae el último estado de advertencia insertado en la pila.  Se deshacen los cambios realizados al estado de la advertencia entre `push` y `pop`.  Considere este ejemplo:  
  
```  
#pragma warning( push )  
#pragma warning( disable : 4705 )  
#pragma warning( disable : 4706 )  
#pragma warning( disable : 4707 )  
// Some code  
#pragma warning( pop )   
```  
  
 Al final de este código, `pop` restaura el estado de cada advertencia \(incluye 4705, 4706 y 4707\) al que tenía al principio del código.  
  
 Cuando escriba archivos de encabezado, puede utilizar `push` y `pop` para garantizar que los cambios realizados por un usuario en el estado de advertencia no impidan que los encabezados se compilen correctamente.  Utilice `push` al principio del encabezado y `pop` al final.  Por ejemplo, si tiene un encabezado que no compila con limpieza en el nivel de advertencia 4, el código siguiente cambiaría el nivel de advertencia a 3 y después restablecería el nivel de advertencia original al final del encabezado.  
  
```  
#pragma warning( push, 3 )  
// Declarations/definitions  
#pragma warning( pop )   
```  
  
 Para obtener más información sobre las opciones del compilador que ayudan a suprimir advertencias, vea [\/FI](../build/reference/fi-name-forced-include-file.md) y [\/w](../build/reference/compiler-option-warning-level.md).  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)