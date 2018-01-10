---
title: -H (restringir la longitud de los nombres externos) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /h
dev_langs: C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d5e862eb8e45d1f2558592c0bb54c1adb9305f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="h-restrict-length-of-external-names"></a>/H (Restringir la longitud de los nombres externos)
Desusado. Restringe la longitud de los nombres externos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Hnumber  
```  
  
## <a name="arguments"></a>Argumentos  
 `number`  
 Especifica la longitud máxima de los nombres externos permitidos en un programa.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, la longitud de los nombres externos (públicos) es de 2.047 caracteres. Esto es cierto para los programas de C y C++. Usar **/H** puede disminuir solo la longitud máxima permitida de identificadores, no demasiado. Un espacio entre **/H** y `number` es opcional.  
  
 Si un programa contiene nombres externos más largos que `number`, los caracteres adicionales se omiten. Si se compila un programa sin **/H** y un identificador contiene más de 2.047 caracteres, el compilador generará [Error irrecuperable C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).  
  
 El límite de longitud incluye cualquier creado por el compilador carácter de subrayado inicial (_) o una arroba (@). Estos caracteres forman parte del identificador y ocupan una ubicación significativa.  
  
-   El compilador agrega un carácter de subrayado (_) inicial a los nombres modificados por la `__cdecl` (valor predeterminado) y `__stdcall` convenciones de llamada e inicial arroba (@) a los nombres modificados por la `__fastcall` convención de llamada.  
  
-   El compilador anexa información de tamaño del argumento a los nombres modificados por la `__fastcall` y `__stdcall` convenciones de llamada y agrega información de tipo a los nombres de C++.  
  
 Es posible **/H** útil:  
  
-   Cuando se crean varios lenguajes o portátiles programas.  
  
-   Cuando se utilizan herramientas que limiten la longitud de los identificadores externos.  
  
-   Si desea restringir la cantidad de espacio que usan los símbolos en una compilación de depuración.  
  
 El siguiente ejemplo se muestra cómo usar **/H** puede causar errores si la longitud de los identificadores es limitados demasiado:  
  
```cpp  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 También debe tener cuidado al usar el **/H** opción debido a los identificadores de compilador predefinidos. Si la longitud máxima del identificador es demasiado pequeña, algunos identificadores predefinidos será biblioteca sin resolver, así como ciertas llamadas a funciones. Por ejemplo, si la `printf` se utiliza la función y la opción **/H5** se especifica en tiempo de compilación, el símbolo **_prin** se creará con el fin de hacer referencia a `printf`, y esto no se encuentre en la biblioteca.  
  
 El uso de **/H** no es compatible con [/GL (optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).  
  
 El **/H** opción está en desuso desde Visual Studio 2005; han aumentado los límites de longitud máxima y **/H** ya no es necesario. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y quitar opciones de compilador** en [opciones de compilador enumerados por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)