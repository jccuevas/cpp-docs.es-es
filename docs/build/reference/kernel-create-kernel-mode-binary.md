---
title: -kernel (Kernel de crear binario en modo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20ea3423acd19a70c5b7b759b9923b0132e04af0
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572770"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Crear binario en modo kernel)
Crea un archivo binario que se puede ejecutar en el kernel de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>Argumentos  
 **/kernel**  
 El código en el proyecto actual se compila y vincula con un conjunto de reglas de lenguaje C++ que son específicas de código que se ejecutará en modo kernel.  
  
 **/kernel-**  
 El código en el proyecto actual se compila y vinculado sin usar las reglas del lenguaje C++ que son específicas de código que se ejecutará en modo kernel.  
  
## <a name="remarks"></a>Comentarios  
 No hay ningún `#pragma` equivalente para controlar esta opción.  
  
 Especificar el **/kernel** opción indica el compilador y vinculador arbitrar qué características de lenguaje están permitidos en modo kernel y para asegurarse de que haya suficiente potencia expresiva para evitar la inestabilidad del tiempo de ejecución que es único para modo de kernel C++. Esto se consigue mediante la prohibición del uso de características del lenguaje C++ que son perjudiciales en modo kernel y proporcionando las advertencias para las características del lenguaje C++ que son potencialmente perjudiciales, pero no se puede deshabilitar.  
  
 El **/kernel** opción se aplica a las fases de compilador y vinculador de una compilación y se establece en el nivel de proyecto. Pase el **/kernel** conmutador para indicar al compilador que el archivo binario resultante, después de la vinculación, se debe cargar en el kernel de Windows. El compilador limitará el espectro de características del lenguaje C++ en un subconjunto que es compatible con el kernel.  
  
 En la tabla siguiente se enumera los cambios de comportamiento del compilador cuando **/kernel** se especifica.  
  
|Tipo de comportamiento|**/kernel** comportamiento|  
|-------------------|---------------------------|  
|Control de excepciones de C++|Deshabilitado. Todas las instancias de la `throw` y `try` palabras clave de emisión de un error del compilador (excepto para la especificación de excepción `throw()`). No **/EH** opciones son compatibles con **/kernel**, excepto para **/EH-**.|  
|RTTI|Deshabilitado. Todas las instancias de la `dynamic_cast` y `typeid` palabras clave de emisión de un error del compilador, a menos que `dynamic_cast` se usa de forma estática.|  
|`new` y `delete`|Debe definir explícitamente el `new()` o `delete()` operador; el compilador ni el tiempo de ejecución que proporcionará una definición default.|  
  
 Custom convenciones de llamada, el [/GS](../../build/reference/gs-buffer-security-check.md) opción de compilación y todas las optimizaciones se permiten cuando se usa el **/kernel** opción. La inserción en gran medida no se ve afectada por **/kernel**, con la misma semántica que cumple con el compilador. Si desea asegurarse de que el `__forceinline` se respeta el calificador de inserción, debe asegurarse de que aparezca esa advertencia [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) está habilitada para que se sabe cuándo un determinado `__forceinline` función no está entre línea.  
  
 Cuando se pasa al compilador la **/kernel** switch, predefine una macro de preprocesador que se denomina `_KERNEL_MODE` y tiene el valor **1**. Puede utilizarlo para compilar condicionalmente en función de si el entorno de ejecución está en modo de usuario o modo núcleo de código. Por ejemplo, el código siguiente especifica que la clase debe estar en un segmento de memoria no paginable cuando se compila para la ejecución en modo kernel.  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
   // ...
};  
```  
  
 Algunos las siguientes combinaciones de arquitectura de destino y el **/arch** opción de generar un error cuando se usan con **/kernel**:  
  
-   **/ arch: {SSE&#124;SSE2&#124;AVX}** no se admiten en x86. Solo **/arch: IA32** es compatible con **/kernel** en x86.  
  
-   **/ arch: AVX** no es compatible con **/kernel** en x64.  
  
 Compilar con **/kernel** también pasa **/kernel** al vinculador. Ella es cómo esto afecta al comportamiento del enlazador:  
  
-   Vinculación incremental deshabilitada. Si agrega **incremental** a la línea de comandos, el vinculador emite este error irrecuperable:  
  
     **LINK: error irrecuperable LNK1295: '/ INCREMENTAL' no es compatible con ' / KERNEL' especificación; vincular sin '/ INCREMENTAL'**  
  
-   El vinculador inspecciona cada archivo de objeto (o cualquier miembro del archivo incluido desde bibliotecas estáticas) para ver si se pudo se han compilado mediante el uso de la **/kernel** opción pero no era. Si todas las instancias cumplen este criterio, el vinculador vincula todavía correctamente pero puede emitir una advertencia, tal como se muestra en la tabla siguiente.  
  
    ||**/kernel** obj|**/kernel-** obj, obj MASM, o cvtresed|Combinación de **/kernel** y **/kernel-** obj|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**vínculo /kernel**|Sí|Sí|Sí con advertencia LNK4257|  
    |**vínculo**|Sí|Sí|Sí|  
  
     **LNK4257 vinculará el objeto que no se compila con/kernel; imagen no se puede ejecutar**  
  
 El **/kernel** opción y la **/driver** opción funcionan de forma independiente y no afecta a la otra.  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador/kernel en Visual Studio  
  
1.  Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C o C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  En el **opciones adicionales** , agregue `/kernel` o `/kernel-`.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)