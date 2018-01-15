---
title: '#Using (directiva) (C++ / CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs: C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8a73eb8e9b5c3f3ba67e4466a6e7138010fd430
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-directive-cclr"></a>#using (directiva) (C++ / CLR)
Importa metadatos en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>Parámetros  
 `file`  
 Archivo .dll, .exe, .netmodule u .obj de MSIL. Por ejemplo,  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 Especifica que todos los tipos de `file` son accesibles.  Para obtener más información, consulte [ensamblados Friend (C++)](../dotnet/friend-assemblies-cpp.md).  
  
## <a name="remarks"></a>Comentarios  
 `file` puede ser un archivo del Lenguaje intermedio de Microsoft (MSIL) que importa para sus datos administrados y construcciones administradas. Si un archivo .dll contiene un manifiesto del ensamblado, a continuación, se importan todos los archivos .dll al que hace referencia en el manifiesto y mostrará el ensamblado que se va a compilar *archivo* en los metadatos como una referencia de ensamblado.  
  
 Si `file` no contiene un ensamblado (si `file` es un módulo) y si no piensa usar la información de tipo del módulo en la aplicación (ensamblado) actual, tiene la posibilidad de indicar que el módulo forma parte del ensamblado; utilice [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Los tipos del módulo estarán disponibles entonces para cualquier aplicación que hiciera referencia al ensamblado.  
  
 Una alternativa al uso `#using` es el [/FU](../build/reference/fu-name-forced-hash-using-file.md) opción del compilador.  
  
 ensamblados .exe pasados a `#using` deben compilarse mediante uno de los compiladores de .NET de Visual Studio (Visual Basic o Visual C#, por ejemplo).  Intentar importar metadatos de un ensamblado .exe compilado con **/CLR** producirá una excepción de carga de archivos.  
  
> [!NOTE]
>  Un componente al que se hace referencia con `#using` puede ejecutarse con una versión diferente del archivo importado en tiempo de compilación, lo que hace que una aplicación cliente proporcione resultados inesperados.  
  
 Para que el compilador reconozca un tipo de un ensamblado (no de un módulo), debe obligársele a que resuelva el tipo, lo que se puede conseguir por ejemplo si se define una instancia del tipo. Existen otras formas de que el compilador resuelva nombres de tipos en un ensamblado; por ejemplo, si se hereda de un tipo de un ensamblado, el compilador reconocerá el nombre del tipo.  
  
 Cuando se importan metadatos compilados a partir de código fuente que utilizó [__declspec (Thread)](../cpp/thread.md), la semántica de subproceso no se conserva en los metadatos. Por ejemplo, una variable declarada con **__declspec (Thread)**, compilado en un programa compilado para .NET Framework common language runtime y, a continuación, se importa a través de `#using`, dejará de tener **__declspec ( subproceso)** semántica en la variable.  
  
 Todos los tipos importados (tanto administrados como nativos) en un archivo al que hace referencia `#using` están disponibles, pero el compilador trata los tipos nativos como declaraciones, no como definiciones.  
  
 automáticamente se hace referencia a mscorlib.dll cuando se compila con **/CLR**.  
  
 La variable de entorno LIBPATH especifica los directorios en los que se busca cuando el compilador intenta resolver los nombres de archivo pasados a `#using`.  
  
 El compilador buscará las referencias en la ruta de acceso siguiente:  
  
-   Una ruta de acceso especificada en la instrucción `#using`.  
  
-   El directorio actual.  
  
-   El directorio del sistema de .NET Framework.  
  
-   Directorios agregados con el [/AI](../build/reference/ai-specify-metadata-directories.md) opción del compilador.  
  
-   Directorios de la variable de entorno LIBPATH.  
  
## <a name="example"></a>Ejemplo  
 Si compila un ensamblado (C) y hace referencia a un ensamblado (B) que a su vez hace referencia a otro ensamblado (A), no tendrá que hacer referencia explícitamente al ensamblado A menos que emplee explícitamente uno de los tipos de A en C.  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>Ejemplo  
  
```  
// using_assembly_B.cpp  
// compile with: /clr /LD  
#using "using_assembly_A.dll"  
public ref class B {  
public:  
   void Test(A a) {}  
   void Test() {}  
};  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, no hay ningún error del compilador por no hacer referencia a using_assembly_A.dll porque el programa no utiliza ninguno de los tipos definidos en using_assembly_A.cpp.  
  
```  
// using_assembly_C.cpp  
// compile with: /clr  
#using "using_assembly_B.dll"  
int main() {  
   B b;  
   b.Test();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)