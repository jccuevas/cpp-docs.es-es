---
title: "/Zc:strictStrings (Deshabilitar conversi&#243;n de tipo de literal de cadena) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:strictStrings"
  - "strictStrings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) (C++)"
  - "/Zc:strictStrings"
  - "strictStrings"
  - "Zc (opción del compilador) (C++)"
  - "-Zc (opción del compilador) (C++)"
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /Zc:strictStrings (Deshabilitar conversi&#243;n de tipo de literal de cadena)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se especifica, el compilador requiere que los punteros inicializados con literales de cadena cumplan estrictamente las cualificaciones de `const`.  
  
## Sintaxis  
  
```  
/Zc:strictStrings[-]  
```  
  
## Comentarios  
 Si se especifica **\/Zc:strictStrings**, el compilador exigirá las cualificaciones de `const` de C\+\+ estándar sobre literales de cadena, como el tipo “matriz de `const` `char`” o “matriz de `const` `wchar_t`”, según la declaración.  Los literales de cadena son inmutables, y si trata de modificar el contenido de uno, se producirá un error de infracción de acceso en tiempo de ejecución.  Debe declarar un puntero de cadena como `const` para inicializarlo con un literal de cadena o usar una `const_cast` explícita para inicializar un puntero no `const`.  De forma predeterminada, o si se especifica **\/Zc:strictStrings\-**, el compilador no exige las cualificaciones de `const` de C\+\+ estándar sobre punteros de cadena inicializados con literales de cadena.  
  
 Utilice la opción **\/Zc:strictStrings** para evitar la compilación de código incorrecto.  En este ejemplo, se muestra cómo un simple error de declaración provoca un bloqueo en tiempo de ejecución:  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 Cuando **\/Zc:strictStrings** está habilitado, el mismo código informa de un error en la declaración de `str`.  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 Si usa `auto` para declarar un puntero de cadena, el compilador creará automáticamente la declaración del tipo de puntero `const` correcta.  Si trata de modificar el contenido de un puntero `const`, el compilador informará de ello en forma de error.  
  
> [!NOTE]
>  La biblioteca de C\+\+ estándar de [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] no admite la opción del compilador **\/Zc:strictStrings** en las compilaciones de depuración.  Si ve varios errores [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) en la salida de la compilación, puede que el motivo sea este.  
  
 Para obtener más información sobre los problemas de conformidad en Visual C\+\+, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir `/Zc:strictStrings` y, luego, elija **Aceptar**.  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)