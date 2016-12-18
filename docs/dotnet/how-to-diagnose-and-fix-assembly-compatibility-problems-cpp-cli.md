---
title: "C&#243;mo: Diagnosticar y resolver los problemas de compatibilidad de los ensamblados (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilidad, entre ensamblados"
  - "excepciones, diagnosticar un comportamiento extraño"
  - "control de versiones"
  - "control de versiones, diagnosticar conflictos"
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Diagnosticar y resolver los problemas de compatibilidad de los ensamblados (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se explica lo que sucede cuando la versión de un ensamblado al que se hace referencia en el tiempo de compilación no coincide con la versión del ensamblado al que se hace referencia en el tiempo de ejecución, y cómo evitar el problema.  
  
 Cuando se compila un ensamblado, se puede hacer referencia a otros ensamblados con la sintaxis `#using`.  Durante la compilación, el compilador tiene acceso a estos ensamblados.  La información de estos ensamblados se utiliza para tomar decisiones de optimización.  
  
 No obstante, si se cambia y compila el ensamblado al que se hace referencia, y no se vuelve a compilar el ensamblado que hace referencia y que es dependiente de él, es posible que los ensamblados sigan sin ser compatibles.  Las decisiones de optimización que eran válidas al principio pueden no ser correctas con respecto a la nueva versión de ensamblado.  Pueden producirse distintos errores en tiempo de ejecución debido a estas incompatibilidades.  No hay ninguna excepción concreta que se genere en casos como éste.  La manera en que se informa del error en tiempo de ejecución depende de la naturaleza del cambio de código que produjo el problema.  
  
 Estos errores no deberían ser un problema en el código de producción final siempre que se recompile toda la aplicación para la versión de lanzamiento del producto.  Los ensamblados que se venden al público deben estar marcados con un número de versión oficial que garantice que se han evitado estos problemas.  Para obtener más información, vea [Versiones de los ensamblados](../Topic/Assembly%20Versioning.md).  
  
### Diagnosticar y corregir un error de incompatibilidad  
  
1.  Si se encuentra con excepciones en tiempo de ejecución u otras condiciones de error que se producen en el código que hace referencia a otro ensamblado, y que no tienen otra causa identificada, es posible que se trate de un ensamblado no actualizado.  
  
2.  En primer lugar, aísle y reproduzca la excepción u otra condición de error.  Un problema que surge debido a una excepción no actualizada debería ser reproducible.  
  
3.  Compruebe la marca de tiempo de cualquier ensamblado al que se hace referencia en la aplicación.  
  
4.  Si las marcas de tiempo de cualquier ensamblado al que se hace referencia son posteriores a la marca de tiempo de la última compilación de la aplicación, entonces la aplicación no está actualizada.  Si ocurre esto, vuelva a compilar la aplicación con el ensamblado más reciente y haga los cambio de código necesarios.  
  
5.  Vuelva a ejecutar la aplicación, siga los pasos que reproducen el problema y compruebe que ya no se produce la excepción.  
  
## Ejemplo  
 El programa siguiente muestra el problema al reducir la accesibilidad de un método e intentar obtener acceso a ese método en otro ensamblado sin volver a compilar.  Intente compilar `changeaccess.cpp` primero.  Éste es el ensamblado al que se hace referencia que cambiará.  A continuación, compile `referencing.cpp`.  La compilación se realiza correctamente.  Ahora, reduzca la accesibilidad del método llamado.  Vuelva a compilar `changeaccess.cpp` con el marcador `/DCHANGE_ACCESS`.  Esto hace que el método sea protegido, en lugar de privado, por lo que se le puede llamar de manera válida durante más tiempo.  Sin volver a compilar `referencing.exe`, vuelva a ejecutar la aplicación.  Se producirá una excepción <xref:System.MethodAccessException>.  
  
```  
// changeaccess.cpp  
// compile with: /clr:safe /LD  
// After the initial compilation, add /DCHANGE_ACCESS and rerun  
// referencing.exe to introduce an error at runtime. To correct  
// the problem, recompile referencing.exe  
  
public ref class Test {  
#if defined(CHANGE_ACCESS)  
protected:  
#else  
public:  
#endif  
  
  int access_me() {  
    return 0;  
  }  
  
};  
  
```  
  
```  
// referencing.cpp  
// compile with: /clr:safe   
#using <changeaccess.dll>  
  
// Force the function to be inline, to override the compiler's own  
// algorithm.  
__forceinline  
int CallMethod(Test^ t) {  
  // The call is allowed only if access_me is declared public  
  return t->access_me();  
}  
  
int main() {  
  Test^ t = gcnew Test();  
  try  
  {  
    CallMethod(t);  
    System::Console::WriteLine("No exception.");  
  }  
  catch (System::Exception ^ e)  
  {  
    System::Console::WriteLine("Exception!");  
  }  
  return 0;  
}  
  
```  
  
## Vea también  
 [\#using \(Directiva\)](../preprocessor/hash-using-directive-cpp.md)   
 [Tipos administrados](../dotnet/managed-types-cpp-cli.md)