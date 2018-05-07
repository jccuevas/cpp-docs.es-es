---
title: 'Cómo: diagnosticar y resolver los problemas de compatibilidad de ensamblados (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4440ab455aff8922c108cdb35cff041cd67f56d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-diagnose-and-fix-assembly-compatibility-problems-ccli"></a>Cómo: Diagnosticar y resolver los problemas de compatibilidad de los ensamblados (C++/CLI)
Este tema explica lo que puede suceder cuando la versión de un ensamblado al que hace referencia en tiempo de compilación no coincide con la versión del ensamblado al que hace referencia en tiempo de ejecución y cómo evitar el problema.  
  
 Cuando se compila un ensamblado, se pueden hacer referencia a otros ensamblados con el `#using` sintaxis. Durante la compilación, se obtiene acceso a estos ensamblados por el compilador. Información de estos ensamblados se utiliza para tomar decisiones de optimización.  
  
 Sin embargo, si se cambia y se vuelve a compilar el ensamblado que se hace referencia, y no se vuelve a compilar el ensamblado de referencia que depende de él, los ensamblados podrían no ser compatible. Las decisiones de optimización que eran válidas en primer lugar pueden no ser correctas con respecto a la nueva versión del ensamblado. Pueden producir varios errores de tiempo de ejecución debido a estas incompatibilidades. No hay ninguna excepción concreta que se producirán en esos casos. La manera en que se notifica el error en tiempo de ejecución depende de la naturaleza del cambio de código que provocó el problema.  
  
 Estos errores no deberían ser un problema en el código de producción final siempre y cuando se vuelve a generar toda la aplicación para la versión de lanzamiento del producto. Los ensamblados que se publican para el público deben marcarse con un número de versión oficial, lo que asegurará que se eviten todos estos problemas. Para obtener más información, vea [Versiones de los ensamblados](/dotnet/framework/app-domains/assembly-versioning).  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnosticar y corregir un error de incompatibilidad  
  
1.  Si encuentra con excepciones en tiempo de ejecución u otras condiciones de error que se producen en el código que hace referencia a otro ensamblado y tener ninguna otra causa identificada, puede tratar con un ensamblado no está actualizado.  
  
2.  En primer lugar, aísle y reproduzca la excepción u otra condición de error. Un problema que se produce debido a una excepción no actualizada debería ser reproducible.  
  
3.  Compruebe la marca de tiempo de cualquier ensamblado al que hace referencia en la aplicación.  
  
4.  Si las marcas de tiempo de todos los ensamblados que se hace referencia son posteriores a la marca de tiempo de la última compilación de la aplicación, la aplicación es obsoleta. Si esto ocurre, vuelva a compilar la aplicación con el ensamblado más reciente y realice los cambios de código necesarios.  
  
5.  Vuelva a ejecutar la aplicación, lleve a cabo los pasos que reproducen el problema y compruebe que no se produce la excepción.  
  
## <a name="example"></a>Ejemplo  
 El programa siguiente muestra el problema al reducir la accesibilidad de un método e intentando obtener acceso a ese método en otro ensamblado sin volver a compilar. Intente compilarla `changeaccess.cpp` primero. Esto es el ensamblado que se hace referencia que cambiará. A continuación, compile `referencing.cpp`. La compilación se realiza correctamente. Ahora, reduzca la accesibilidad del método llamado. Volver a compilar `changeaccess.cpp` con la marca `/DCHANGE_ACCESS`. Esto hace que el método protegido, en lugar de privado, por lo que ya puede llamarse legalmente. Sin tener que recompilar `referencing.exe`, vuelva a ejecutar la aplicación. Una excepción <xref:System.MethodAccessException> dará como resultado.  
  
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
  
## <a name="see-also"></a>Vea también  
 [#using (directiva)](../preprocessor/hash-using-directive-cpp.md)   
 [Tipos administrados (C++/CLI)](../dotnet/managed-types-cpp-cli.md)