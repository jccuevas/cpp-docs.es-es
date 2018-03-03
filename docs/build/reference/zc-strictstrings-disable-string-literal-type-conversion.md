---
title: "-Zc: strictStrings (deshabilitar conversión de tipo de literal de cadena) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs:
- C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f316c5fc9209f968219d770a15e6576880b69954
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Deshabilitar conversión de tipo de literal de cadena)
Cuando se especifica, el compilador requiere que los punteros inicializados con literales de cadena cumplan estrictamente las cualificaciones de `const`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Zc:strictStrings[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 Si **/Zc: strictstrings** se especifica, el compilador exige el estándar de C++ `const` calificación para literales de cadena, como el tipo ' matriz de `const char`' o ' matriz de `const wchar_t`', en función de la declaración. Los literales de cadena son inmutables, y si trata de modificar el contenido de uno, se producirá un error de infracción de acceso en tiempo de ejecución. Debe declarar un puntero de cadena como `const` para inicializarlo con un literal de cadena o usar una `const_cast` explícita para inicializar un puntero no `const`. De forma predeterminada, o si **/Zc:strictStrings-** se especifica, el compilador no exige el estándar de C++ `const` calificación para punteros de cadena inicializados con literales de cadena.  
  
 Use la **/Zc: strictstrings** opción para evitar la compilación de código incorrecto. En este ejemplo, se muestra cómo un simple error de declaración provoca un bloqueo en tiempo de ejecución:  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 Cuando **/Zc: strictstrings** está habilitada, el mismo código informa de un error en la declaración de `str`.  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 Si usa `auto` para declarar un puntero de cadena, el compilador creará automáticamente la declaración del tipo de puntero `const` correcta. Si trata de modificar el contenido de un puntero `const`, el compilador informará de ello en forma de error.  
  
> [!NOTE]
>  La biblioteca estándar de C++ en [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] no admite el **/Zc: strictstrings** compilaciones de la opción del compilador en versiones de depuración. Si ve varios [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) errores en la compilación de salida, esto puede ser la causa.  
  
 Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Modificar el **opciones adicionales** propiedad para incluir `/Zc:strictStrings` y, a continuación, elija **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [/Zc (ajuste)](../../build/reference/zc-conformance.md)