---
title: '#Using (directiva) (C++ / c++ / CLI)'
ms.date: 10/18/2018
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: d69b06d29c366d0ff9c525421311001cab4e501c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501106"
---
# <a name="using-directive-ccli"></a>#using (directiva) (C++ / c++ / CLI)

Importa metadatos en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Sintaxis

```
#using file [as_friend]
```

### <a name="parameters"></a>Parámetros

*file*<br/>
Archivo .dll, .exe, .netmodule u .obj de MSIL. Por ejemplo,

`#using <MyComponent.dll>`

*as_friend*<br/>
Especifica que todos los tipos en *archivo* son accesibles. Para obtener más información, consulte [ensamblados Friend (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Comentarios

*archivo* puede ser un archivo de lenguaje intermedio (MSIL) de Microsoft que se importa para sus datos administrados y construcciones administradas. Si un archivo .dll contiene un manifiesto del ensamblado, a continuación, se importan todos los archivos .dll que se hace referencia en el manifiesto y mostrará una lista el ensamblado que está compilando *archivo* en los metadatos como una referencia de ensamblado.

Si *archivo* no contiene un ensamblado (si *archivo* es un módulo) y si no piensa usar la información de tipo del módulo en la aplicación (ensamblado) actual, tiene la opción de lo que indica que el módulo forma parte del ensamblado; usar [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Los tipos del módulo estarán disponibles entonces para cualquier aplicación que hiciera referencia al ensamblado.

Una alternativa al uso **#using** es el [/FU](../build/reference/fu-name-forced-hash-using-file.md) opción del compilador.

los ensamblados .exe pasados a **#using** deben compilarse mediante uno de los compiladores .NET de Visual Studio (Visual Basic o Visual C#, por ejemplo).  Si se intenta importar metadatos de un ensamblado .exe compilado con `/clr`, se producirá una excepción de carga del archivo.

> [!NOTE]
> Un componente que se hace referencia con **#using** se pueden ejecutar con una versión diferente del archivo importado en tiempo de compilación, provocando una aplicación cliente para proporcionar resultados inesperados.

Para que el compilador reconozca un tipo de un ensamblado (no de un módulo), debe obligársele a que resuelva el tipo, lo que se puede conseguir por ejemplo si se define una instancia del tipo. Existen otras formas de que el compilador resuelva nombres de tipos en un ensamblado; por ejemplo, si se hereda de un tipo de un ensamblado, el compilador reconocerá el nombre del tipo.

Cuando se importan metadatos compilados a partir de código fuente que utilizó [__declspec (Thread)](../cpp/thread.md), la semántica de subproceso no se conserva en los metadatos. Por ejemplo, una variable declarada con **__declspec (Thread)**, compilado en un programa compilado para .NET Framework common language runtime e importada después mediante **#using**, dejará de tener **__declspec (Thread)** semántica en la variable.

Todos los tipos (administrados y nativos) en un archivo al que hace referencia importados **#using** están disponibles, pero el compilador trata los tipos nativos como declaraciones no las definiciones.

Se hace referencia automáticamente a mscorlib.dll cuando se compila con `/clr`.

La variable de entorno LIBPATH especifica los directorios que se buscarán cuando el compilador intenta resolver los nombres de archivo que se pasan a **#using**.

El compilador buscará las referencias en la ruta de acceso siguiente:

- Una ruta de acceso especificada en el **#using** instrucción.

- El directorio actual.

- El directorio del sistema de .NET Framework.

- Directorios agregados con el [/AI](../build/reference/ai-specify-metadata-directories.md) opción del compilador.

- Directorios de la variable de entorno LIBPATH.

## <a name="example"></a>Ejemplo

Si compila un ensamblado (C) y hace referencia a un ensamblado (B) que a su vez hace referencia a otro ensamblado (A), no tendrá que hacer referencia explícitamente al ensamblado A menos que emplee explícitamente uno de los tipos de A en C.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>Ejemplo

```cpp
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

```cpp
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