---
title: "/kernel (Crear binario en modo kernel) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/kernel"
  - "/kernel-"
dev_langs: 
  - "C++"
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /kernel (Crear binario en modo kernel)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un binario que se puede ejecutar en el kernel de Windows.  
  
## Sintaxis  
  
```  
/kernel[-]  
```  
  
## Argumentos  
 **\/kernel**  
 El código del proyecto actual se compila y se vincula con un conjunto de reglas del lenguaje C\+\+ específicas al código que se ejecutará en modo kernel.  
  
 **\/kernel\-**  
 El código del proyecto actual se compila y se vincula sin utilizar las reglas del lenguaje C\+\+ específicas del código que se ejecutará en modo kernel.  
  
## Comentarios  
 No hay equivalente de `#pragma` para controlar esta opción.  
  
 Especificando la opción de **\/kernel** indica al compilador y el vinculador que arbitren las características de lenguaje son permitidas en modo kernel y asegurarse de que tiene suficiente potencia expresivo para evitar la inestabilidad en tiempo de ejecución que es única en modo kernel C\+\+.  Esto se logra prohibiendo el uso de las características del lenguaje C\+\+ que son que interfieren con en modo kernel y proporcionando las advertencias para las características del lenguaje C\+\+ que son potencialmente que interfieren con pero no se puede deshabilitar.  
  
 La opción de **\/kernel** se aplica a las fases del compilador y el vinculador de una compilación y se establece en el nivel de proyecto.  Pase el modificador **\/kernel** para indicar al compilador que el binario resultante, después de vincular, se debe cargar en el kernel de Windows.  El compilador estrechará el espectro de características del lenguaje C\+\+ un subconjunto que sea compatible con el kernel.  
  
 La tabla siguiente se indican los cambios de comportamiento del compilador cuando se especifica **\/kernel** .  
  
|Tipo de comportamiento|comportamiento de**\/kernel**|  
|----------------------------|-----------------------------------|  
|Control de excepciones de C\+\+|Deshabilitado.  Todas las instancias de las palabras clave de `throw` y de `try` emite un error del compilador \(a excepción de la especificación `throw()`de la excepción.  No hay opciones de **\/EH** compatibles con **\/kernel**, a excepción de **\/EH\-**.|  
|RTTI|Deshabilitado.  Todas las instancias de las palabras clave de `dynamic_cast` y de `typeid` emite un error del compilador, a menos que `dynamic_cast` se utilice estáticamente.|  
|`new` y `delete`|Debe definir explícitamente el operador de `new()` o de `delete()` ; ni el compilador ni el runtime proporcionará una definición predeterminada.|  
  
 Las convenciones de llamada personalizadas, [\/GS](../../build/reference/gs-buffer-security-check.md) compilan la opción, y se permiten todas las optimizaciones al utilizar la opción **\/kernel** .  Inclusión no afecta en gran medida por **\/kernel**, con la misma semántica honrada por el compilador.  Si desea asegurarse de que `__forceinline` inclusión el calificador se tendrá en cuenta, debe asegurarse de que la advertencia de [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) esté habilitado para saber cuándo una función de `__forceinline` de detalle no insertadas.  
  
 Cuando el compilador se pasa el modificador **\/kernel** , predefine una macro de preprocesador denominado `_KERNEL_MODE` y tiene el valor **1**.  Puede utilizar esto para compilar condicionalmente el código basándose en el entorno de ejecución está en modo de usuario o modo kernel.  Por ejemplo, el código siguiente especifica que la clase debe estar en un segmento que no se puede controlar por páginas de memoria cuando se compila para la ejecución en modo kernel.  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
  
};  
  
```  
  
 Algunos combinaciones siguientes de arquitectura de destino y la opción de **\/arch** genera un error cuando se utilizan con **\/kernel**:  
  
-   **\/arch:{SSE&#124;SSE2&#124;AVX}** no se admite en x86.  Sólo **\/arch:IA32** se admite con **\/kernel** en x86.  
  
-   **\/arch:AVX** no se admite con **\/kernel** en x64.  
  
 La compilación mediante **\/kernel** pasa también **\/kernel** al vinculador.  Her cómo esto afecta al comportamiento del vinculador:  
  
-   Se deshabilita la vinculación incremental.  Si agrega **\/incremental** a la línea de comandos, el vinculador emite este error irrecuperable:  
  
     **LINK : fatal error LNK1295: '\/INCREMENTAL' not compatible with '\/KERNEL' specification; link without '\/INCREMENTAL'**  
  
-   El vinculador inspecciona cada archivo objeto \(o a cualquier miembro incluido del archivo de bibliotecas estáticas\) para ver si podría haberse compilado mediante la opción de **\/kernel** pero no.  Si algunas instancias cumplen este criterio, todavía del vinculador vínculos correctamente pero pueden emitir una advertencia, como se muestra en la tabla siguiente.  
  
    ||obj de**\/kernel**|obj de**\/kernel\-** , obj de MASM, o cvtresed|Combinación de **\/kernel** y de objs de **\/kernel\-**|  
    |-|------------------------|----------------------------------------------------|-------------------------------------------------------------|  
    |**vínculo \/kernel**|Sí|Sí|Sí con la advertencia de LNK4257|  
    |**link**|Sí|Sí|Sí|  
  
     **LNK4257 linking object not compiled with \/KERNEL ; image may not run**  
  
 La opción de **\/kernel** y la opción de **\/driver** funcionan independientemente y no afecta al otro.  
  
### Para establecer la opción del compilador \/kernel en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  En el cuadro de **Opciones adicionales** , agregue `/kernel` o `/kernel-`.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)