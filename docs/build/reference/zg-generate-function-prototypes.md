---
title: "-Zg (generar prototipos de función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zg
dev_langs: C++
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03e42c32806bbe7142b8d4d03e2f0974eeacdf84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zg-generate-function-prototypes"></a>/Zg (Generar prototipos de función)
Quitado. Crea un prototipo de función para cada función definida en el archivo de origen, pero no compila el archivo de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zg  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción de compilador ya no está disponible. Se quitó en Visual C++ 2015. Esta página se conserva para usuarios de versiones anteriores de Visual C++.  
  
 El prototipo de función incluye el tipo de valor devuelto de función y una lista de tipos de argumento. La lista de tipos de argumento se crea a partir de los tipos de los parámetros formales de la función. Se omiten los prototipos de función ya presentes en el archivo de origen.  
  
 La lista de prototipos se escribe en la salida estándar. Esta lista puede resultarle útil para comprobar que los argumentos reales y los parámetros formales de una función son compatibles. Para guardar la lista, redirija la salida estándar a un archivo. A continuación, puede usar **#include** para que la lista de prototipos de función forme parte del archivo de origen. Al hacerlo, el compilador realizará una comprobación de tipos de argumento.  
  
 Si usa la opción **/Zg** y el programa contiene parámetros formales con los tipos struct, enum o union (o punteros a estos tipos), la declaración de cada tipo struct, enum o union debe tener una etiqueta (nombre). En el ejemplo siguiente, el nombre de etiqueta es `MyStruct`.  
  
```C  
// Zg_compiler_option.c  
// compile with: /Zg  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```  
  
 El **/Zg** opción ha quedado obsoleta en Visual Studio 2005 y se ha quitado en Visual Studio 2015. El compilador de Visual C++ quitó la compatibilidad con el código anterior, de estilo C. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y quitar opciones de compilador** en [opciones de compilador enumerados por categoría](../../build/reference/compiler-options-listed-by-category.md).  
  
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